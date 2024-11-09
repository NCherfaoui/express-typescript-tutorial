# Configuration initiale

Cette section vous guidera à travers les étapes nécessaires pour configurer votre environnement de développement pour un projet Express avec TypeScript.

## Prérequis

Assurez-vous d'avoir installé :
- Node.js (version 12 ou supérieure)
- npm (généralement installé avec Node.js)

## Étapes de configuration

### 1. Initialisation du projet

Créez un nouveau dossier pour votre projet et initialisez-le :

```bash
mkdir mon-projet-express-ts
cd mon-projet-express-ts
npm init -y
```

### 2. Installation des dépendances

Installez les dépendances nécessaires :

```bash
npm install express
npm install --save-dev typescript @types/express @types/node ts-node nodemon
```

### 3. Configuration de TypeScript

Créez un fichier `tsconfig.json` à la racine de votre projet :

```json
{
  "compilerOptions": {
    "target": "es6",
    "module": "commonjs",
    "outDir": "./dist",
    "rootDir": "./src",
    "strict": true,
    "esModuleInterop": true,
    "skipLibCheck": true,
    "forceConsistentCasingInFileNames": true
  },
  "include": [
    "src/**/*"
  ],
  "exclude": [
    "node_modules",
    "**/*.spec.ts"
  ]
}
```

### 4. Structure du projet

Créez la structure de dossiers suivante :

```
mon-projet-express-ts/
├── src/
│   └── server.ts
├── package.json
└── tsconfig.json
```
Voir en détail la section [Structure du projet](2_project-structure.md)

### 5. Scripts npm

Ajoutez les scripts suivants à votre `package.json` :

```json
"scripts": {
  "start": "node dist/server.js",
  "dev": "nodemon src/server.ts",
  "build": "tsc -p ."
}
```

Votre environnement est maintenant configuré pour développer une application Express avec TypeScript !

Dans la prochaine section, nous allons voir comment structurer notre projet.

[Structure du projet](2_project-structure.md)
  