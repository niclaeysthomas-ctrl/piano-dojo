# Piano Dojo

Apprendre le piano **par la théorie, sans solfège** — et travailler sa **voix**. Application web mobile-first, un seul fichier, aucune dépendance.

## Utiliser

Ouvre le lien GitHub Pages sur ton téléphone → **« Ajouter à l'écran d'accueil »**. La progression est sauvegardée dans le navigateur (localStorage) ; garde le même appareil/navigateur pour la retrouver.

## Contenu

- **Parcours** : 8 modules / 18 leçons (fondations → renversements → degrés → main gauche → rythme → accords de 7e → gammes & impro → oreille), chaque leçon = théorie + exercice validé sur clavier virtuel.
- **Dojo** : 10 salles d'entraînement à déblocage progressif, dont une **session mixte** qui s'enrichit à chaque leçon validée.
- **Voix** 🎤 : justesse (détection de hauteur au micro), tessiture, échauffement guidé, diction (virelangues au métronome), souffle.
- **Outils** : clavier libre, métronome, aide-mémoire, stats.

Gamification : XP, grades ceintures, séries, records. Les exercices Voix marqués 🎤 utilisent le micro pour détecter la hauteur — rien n'est enregistré ni envoyé.

## Technique

`index.html` autonome. Audio synthétisé via Web Audio API. Détection de hauteur par autocorrélation du signal micro. Données locales (localStorage).
