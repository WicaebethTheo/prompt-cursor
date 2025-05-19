# Projet de Tableau de Matchs pour Tournoi Valorant

## Description Générale
Une application web Next.js qui affiche un tableau de matchs pour un tournoi esport Valorant. L'application présente un design moderne et thématique inspiré de l'univers Valorant, avec une interface personnalisable permettant de changer les équipes, les logos, la carte Valorant affichée et d'autres détails du tournoi.

## Technologies Utilisées
- **Framework Frontend**: Next.js 13.4.12
- **Langage**: JavaScript/React 18.2.0
- **Styling**: Tailwind CSS 3.2.0
- **Icônes**: Lucide React 0.244.0
- **Environnement**: Node.js (>=14.x)
- **Gestionnaire de Paquets**: npm

## Structure du Projet
```
/valorant-tournament/
├── .next/                 # Dossier de build Next.js
├── app/                   # Pages et routage Next.js
│   ├── admin/             # Interface d'administration
│   │   └── page.jsx       # Page d'administration
│   ├── favicon.ico        # Icône du site
│   ├── globals.css        # Styles CSS globaux
│   ├── layout.jsx         # Layout principal de l'application
│   └── page.jsx           # Page principale
├── components/            # Composants React réutilisables
│   ├── MatchItem.jsx      # Composant pour un match individuel
│   ├── TournamentBracket.jsx # Composant principal du tableau
│   └── TournamentConfig.jsx  # Composant de configuration
├── node_modules/          # Dépendances installées
├── public/                # Assets statiques
│   └── team-logos/        # Logos des équipes (si hébergés localement)
├── utils/                 # Fonctions utilitaires
│   ├── tournamentData.js  # Données du tournoi
│   └── TournamentContext.jsx # Contexte React pour la gestion de l'état
├── .gitignore             # Fichiers à ignorer par Git
├── eslint.config.mjs      # Configuration ESLint
├── next-env.d.ts          # Types pour Next.js
├── next.config.js         # Configuration Next.js
├── package-lock.json      # Verrouillage des versions des dépendances
├── package.json           # Dépendances et scripts
├── postcss.config.js      # Configuration PostCSS
├── postcss.config.mjs     # Configuration PostCSS alternative
├── README.md              # Documentation du projet
├── tailwind.config.js     # Configuration Tailwind CSS
└── tsconfig.json          # Configuration TypeScript
```

## Thèmes et Couleurs
L'application utilise une palette de couleurs inspirée de Valorant :

- **Couleur Principale**: Orange vif (#FF7F27) pour les titres et les noms d'équipes
- **Arrière-plan**: Images des cartes Valorant légèrement assombries
- **Palette de couleurs pour les logos**:
  - Saumon: #f35f91
  - Rose: #ec4899
  - Violet: #8a5cf7
  - Jaune: #ffc973
  - Corail: #f79e71

## Fonctionnalités Principales

### 1. Affichage du Tableau de Matchs
- Affichage de 8 matchs avec le format suivant:
  * Logo de l'équipe 1 | Nom de l'équipe 1 | VS | Logo de l'équipe 2 | Nom de l'équipe 2
  * Fond orange pour les noms d'équipes
  * Logos dans des carrés colorés
- Date du tournoi affichée en haut
- Titre "SUMMER TOURNAMENT" en orange vif
- Sous-titre indiquant le type de match (ex: "1ER MATCHS DES POULES (14H00)")

### 2. Affichage Thématique de la Carte
- Nom de la carte Valorant (ex: "SPLIT") affiché en grand texte vertical sur le côté gauche
- Arrière-plan thématique basé sur l'image de la carte sélectionnée

### 3. Sélection Interactive de Carte
- Bouton "CHANGER DE MAP" en haut à droite
- Interface de sélection permettant de choisir parmi 11 cartes Valorant disponibles:
  * ASCENT
  * BIND
  * BREEZE
  * FRACTURE
  * HAVEN
  * ICEBOX
  * LOTUS
  * PEARL
  * SPLIT
  * SUNSET
  * ABYSS

### 4. Administration et Personnalisation
- Interface d'administration accessible via /admin
- Possibilité de modifier:
  * Titre du tournoi
  * Date du tournoi
  * Sous-titre
  * Carte Valorant affichée
  * Équipes participantes et leurs logos
  * Capitaines des équipes

### 5. Gestion des Données
- Système de sauvegarde et chargement des configurations de tournoi
- Structure de données flexible pour les matchs et équipes
- Intégration d'images via URLs pour une maintenance simplifiée

## Composants Clés

### TournamentBracket.jsx
Composant principal qui affiche le tableau complet des matchs. Il gère:
- L'affichage du titre et de la date
- Le positionnement vertical du nom de la carte
- L'organisation des matchs en liste
- Le fond d'écran thématique basé sur la carte

### MatchItem.jsx
Composant qui affiche un match individuel avec:
- Les logos des deux équipes
- Les noms des équipes sur fond orange
- L'indicateur "VS" entre les équipes
- Les capitaines des équipes (si configurés)

### TournamentConfig.jsx
Interface d'administration permettant de:
- Modifier les informations générales du tournoi
- Sélectionner la carte Valorant
- Configurer les équipes et leurs matchs
- Sauvegarder et charger des configurations

### TournamentContext.jsx
Gestion de l'état global de l'application via React Context:
- Sauvegarde des données du tournoi
- Mise à jour des informations en temps réel
- Persistance des données entre les sessions

## Structure des Données

Le fichier `tournamentData.js` contient la configuration complète du tournoi:

```javascript
{
  title: "SUMMER TOURNAMENT",
  date: "25 & 26 MAI 2025",
  subtitle: "1ER MATCHS DES POULES (14H00)",
  map: {
    name: "SPLIT",
    backgroundImage: "https://cmsassets.rgpub.io/..."
  },
  matches: [
    {
      team1: {
        name: "FNATIC",
        logo: "https://upload.wikimedia.org/...",
        logoBackground: "#f35f91",
        captain: "BOASTER"
      },
      team2: {
        name: "G2 ESPORTS",
        logo: "https://upload.wikimedia.org/...",
        logoBackground: "#ec4899",
        captain: "MIXWELL"
      }
    },
    // 7 autres matchs configurés de manière similaire
  ],
  // Liste des cartes Valorant disponibles
  availableMaps: [
    { name: "ASCENT", backgroundImage: "https://beebom.com/..." },
    // 10 autres cartes configurées
  ]
}
```

## Installation et Démarrage

### Prérequis
- Node.js >=14.x
- npm

### Installation
```bash
# Cloner le dépôt
git clone [URL_DU_REPO]

# Installer les dépendances
cd valorant-tournament
npm install

# Démarrer le serveur de développement
npm run dev
```

L'application sera accessible à l'adresse http://localhost:3000

## Personnalisation

### Modification des Données du Tournoi
1. **Via l'interface d'administration**:
   - Accédez à http://localhost:3000/admin
   - Utilisez l'interface pour modifier les paramètres

2. **Modification directe du fichier de données**:
   - Éditez le fichier `utils/tournamentData.js`
   - Redémarrez l'application pour appliquer les changements

### Ajout de Logos d'Équipes
- Option 1: Utiliser des URLs d'images externes (méthode actuelle)
- Option 2: Ajouter des images dans le dossier `public/team-logos/` et référencer en chemin relatif

### Modification de l'Interface
- Les styles principaux sont définis dans `app/globals.css`
- La mise en page du tableau est configurée dans `components/TournamentBracket.jsx`
- Les styles des matchs individuels sont configurés dans `components/MatchItem.jsx`

## Déploiement
Pour déployer l'application en production:

```bash
# Construire l'application pour la production
npm run build

# Démarrer l'application en mode production
npm start
```

Ou utiliser la plateforme Vercel pour un déploiement simplifié:
1. Connectez votre dépôt GitHub à Vercel
2. Suivez les instructions pour déployer

## Extensions Futures Possibles
1. Ajout d'un système d'authentification pour l'administration
2. Historique des tournois précédents
3. Intégration avec une API Valorant pour récupérer des données en temps réel
4. Support pour différents formats de tournois (élimination directe, phases de groupes)
5. Mode sombre/clair
6. Adaptation pour mobile
7. Animation lors du changement de carte

## Conclusions
Ce projet fournit une solution complète et visuellement attrayante pour l'affichage de tableaux de matchs pour les tournois Valorant. Sa structure modulaire et sa configuration flexible permettent une adaptation facile à différents événements esports. 