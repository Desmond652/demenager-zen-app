# demenager-zen-app
Application web “Déménager Zen Europe”
{
  "name": "demenager-zen-app",
  "version": "0.1.0",
  "private": true,
  "dependencies": {
    "react": "^18.0.0",
    "react-dom": "^18.0.0",
    "react-scripts": "5.0.1"
  },
  "scripts": {
    "start": "react-scripts start",
    "build": "react-scripts build",
    "test": "react-scripts test",
    "eject": "react-scripts eject"
  }
}
import { useState } from "react";
function App() {
  const [step, setStep] = useState(0);
  const [city, setCity] = useState("");
  const [moveDate, setMoveDate] = useState("");
  const checklist = [
    "Prendre date du déménagement",
    "Informer le propriétaire / syndic",
    "Résilier internet et énergie",
    "Trier / jeter / donner"
  ];
  return (
    <div style={{ maxWidth: '600px', margin: '40px auto', fontFamily: 'Arial, sans-serif' }}>
      <h1>Déménager Zen Europe</h1>
      {step === 0 && (
        <>
          <p>Où vas-tu déménager ?</p>
          <input value={city} onChange={e => setCity(e.target.value)} placeholder="Ex: Bruxelles" />
          <p>Date de déménagement :</p>
          <input type="date" value={moveDate} onChange={e => setMoveDate(e.target.value)} />
          <button onClick={() => setStep(1)}>Générer mon plan</button>
        </>
      )}
      {step === 1 && (
        <>
          <h2>Checklist pour {city} le {moveDate}</h2>
          <ul>
            {checklist.map((it, i) => <li key={i}>{it}</li>)}
          </ul>
          <button onClick={() => setStep(2)}>Voir les modèles de courriers</button>
        </>
      )}
      {step === 2 && (
        <>
          <h2>Modèles utiles</h2>
          <ul>
            <li>Lettre de résiliation de bail</li>
            <li>Lettre de changement d'adresse</li>
            <li>Email de notification employeur/école</li>
          </ul>
          <button onClick={() => setStep(3)}>Voir le budget & bonus</button>
        </>
      )}
      {step === 3 && (
        <>
          <h2>Plan de budget & bonus</h2>
          <ul>
            <li>Liste des dépenses à prévoir</li>
            <li>Conseils pour économiser</li>
            <li>5 erreurs à éviter</li>
            <li>Script WhatsApp prêt</li>
          </ul>
          <button onClick={() => setStep(0)}>Recommencer</button>
        </>
      )}
    </div>
  );
}
export default App;

demenager-zen-app/
  ├── package.json
  ├── public/
  │    └── index.html
  └── src/
       ├── App.js
       └── index.js
