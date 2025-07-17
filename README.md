import { useState } from "react";
import { Card, CardContent } from "@/components/ui/card";
import { Button } from "@/components/ui/button";
import { Input } from "@/components/ui/input";
import { Calendar } from "@/components/ui/calendar";

export default function DemenagerZenApp() {
  const [step, setStep] = useState(0);
  const [city, setCity] = useState("");
  const [moveDate, setMoveDate] = useState(null);
  const [checklist, setChecklist] = useState([
    "Prendre date du déménagement",
    "Informer le propriétaire / syndic",
    "Résilier internet et énergie",
    "Trier / jeter / donner",
  ]);

  return (
    <div className="p-4 max-w-2xl mx-auto">
      <h1 className="text-3xl font-bold mb-4">Déménager Zen Europe</h1>
      <Card className="mb-4">
        <CardContent>
          {step === 0 && (
            <div className="space-y-4">
              <p className="text-lg">Où vas-tu déménager ?</p>
              <Input
                placeholder="Exemple : Bruxelles"
                value={city}
                onChange={(e) => setCity(e.target.value)}
              />
              <p className="text-lg">Date de déménagement :</p>
              <Calendar mode="single" selected={moveDate} onSelect={setMoveDate} />
              <Button onClick={() => setStep(1)}>Générer mon plan</Button>
            </div>
          )}

          {step === 1 && (
            <div className="space-y-4">
              <p className="text-lg font-semibold">
                Checklist personnalisée pour ton déménagement à {city} le {moveDate?.toLocaleDateString()}
              </p>
              <ul className="list-disc pl-5 space-y-1">
                {checklist.map((item, i) => (
                  <li key={i}>{item}</li>
                ))}
              </ul>
              <Button className="mt-4" onClick={() => setStep(2)}>
                Voir les modèles d'emails et courriers
              </Button>
            </div>
          )}

          {step === 2 && (
            <div className="space-y-4">
              <p className="text-lg font-semibold">Modèles utiles :</p>
              <ul className="list-disc pl-5 space-y-1">
                <li>Lettre de résiliation de bail</li>
                <li>Lettre de changement d'adresse</li>
                <li>Emails pour prévenir ton employeur, ton école...</li>
              </ul>
              <Button className="mt-4" onClick={() => setStep(3)}>
                Voir le plan de budget & les bonus
              </Button>
            </div>
          )}

          {step === 3 && (
            <div className="space-y-4">
              <p className="text-lg font-semibold">Plan de budget & bonus :</p>
              <ul className="list-disc pl-5 space-y-1">
                <li>Liste de dépenses à prévoir</li>
                <li>Conseils pour économiser sur le transport</li>
                <li>5 erreurs à éviter qui coûtent cher</li>
                <li>Script WhatsApp prêt à copier</li>
              </ul>
              <Button className="mt-4" onClick={() => setStep(0)}>
                Recommencer
              </Button>
            </div>
          )}
        </CardContent>
      </Card>
    </div>
  );
}

