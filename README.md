<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Analyseur de Phrases Toxiques</title>
  <style>
    /* Réinitialisation des marges et du padding */
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    /* Corps de la page */
    body {
      font-family: Arial, sans-serif;
      background-color: #f4f4f4;
      color: #333;
      padding: 20px;
    }

    /* En-tête */
    header {
      background-color: #333;
      color: white;
      padding: 20px;
      text-align: center;
    }

    /* Section de formulaire */
    #form-section {
      background-color: white;
      padding: 20px;
      border-radius: 8px;
      margin: 20px 0;
    }

    textarea {
      width: 100%;
      padding: 10px;
      font-size: 16px;
      margin-bottom: 10px;
      border-radius: 5px;
      border: 1px solid #ccc;
    }

    button {
      padding: 10px 20px;
      background-color: #333;
      color: white;
      border: none;
      border-radius: 5px;
      cursor: pointer;
    }

    button:hover {
      background-color: #555;
    }

    /* Section des résultats */
    #resultats-section {
      background-color: white;
      padding: 20px;
      border-radius: 8px;
      margin: 20px 0;
    }

    #resultats {
      font-family: Courier, monospace;
      white-space: pre-wrap;
    }

    /* Pied de page */
    footer {
      text-align: center;
      padding: 10px;
      background-color: #333;
      color: white;
      position: fixed;
      width: 100%;
      bottom: 0;
    }
  </style>
</head>
<body>
  <header>
    <h1>Analyseur de Phrases Toxiques</h1>
  </header>

  <main>
    <section id="form-section">
      <h2>Entrez vos phrases à analyser :</h2>
      <textarea id="phrases-input" rows="6" cols="50" placeholder="Entrez vos phrases ici..."></textarea><br>
      <button onclick="analyserPhrases()">Analyser les phrases</button>
    </section>

    <section id="resultats-section">
      <h2>Résultats de l'analyse :</h2>
      <div id="resultats"></div>
    </section>
  </main>

  <footer>
    <p>&copy; 2025 Mon Site Web</p>
  </footer>

  <script>
    // Liste de mots toxiques
    const motsToxiques = [
      "connard", "idiot", "imbécile", "crétin", "salaud", "trou du cul", "enculé", "bâtard", "pute", "salope",
      "fils de pute", "sale con", "débile", "stupide", "tête de noeud", "fou", "taré", "merdeux", "merde",
      "con", "connasse", "abruti", "baltringue", "fainéant", "gros naze", "pouffiasse", "clochard", "cloche",
      "tarlouze", "pédé", "pd", "sale pute", "niqué", "cocu", "bordel", "salaud", "vieux con", "bavard", "fayot"
    ];

    // Fonction pour analyser les phrases et détecter les mots toxiques
    function analyserPhrases() {
      const phrasesInput = document.getElementById('phrases-input').value;
      const phrases = phrasesInput.split('\n'); // On sépare les phrases par des retours à la ligne
      const resultatsDiv = document.getElementById('resultats');
      resultatsDiv.innerHTML = ''; // Réinitialiser les résultats

      phrases.forEach(phrase => {
        const phraseMinuscule = phrase.toLowerCase(); // Conversion en minuscule pour comparaison
        let phraseResultat = `La phrase : '${phrase}' n'est pas toxique.`;

        // Vérifier si un mot toxique est présent dans la phrase
        if (motsToxiques.some(mot => phraseMinuscule.includes(mot))) {
          phraseResultat = `La phrase : '${phrase}' est toxique.`;
        }

        // Afficher le résultat
        resultatsDiv.innerHTML += `${phraseResultat}\n`;
      });
    }
  </script>
</body>
</html>

