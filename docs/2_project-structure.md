# Structure du projet

Une bonne structure de projet est essentielle pour maintenir votre application Express avec TypeScript organisée et évolutive. Voici une structure recommandée pour un projet de taille moyenne :

```
mon-projet-express-ts/
├── src/
│   ├── config/
│   │   └── database.ts
│   ├── controllers/
│   │   ├── userController.ts
│   │   └── productController.ts
│   ├── models/
│   │   ├── User.ts
│   │   └── Product.ts
│   ├── routes/
│   │   ├── index.ts
│   │   ├── userRoutes.ts
│   │   └── productRoutes.ts
│   ├── middleware/
│   │   ├── errorHandler.ts
│   │   └── auth.ts
│   ├── services/
│   │   ├── userService.ts
│   │   └── productService.ts
│   ├── utils/
│   │   └── logger.ts
│   ├── types/
│   │   └── custom.d.ts
│   └── server.ts
├── tests/
│   ├── unit/
│   └── integration/
├── dist/
├── logs/
├── .env
├── .env.example
├── .gitignore
├── package.json
├── tsconfig.json
└── README.md
```

## Explication de la structure

- `src/`: Contient tout le code source de l'application.
  - `config/`: Fichiers de configuration (base de données, variables d'environnement, etc.).
  - `controllers/`: Logique de traitement des requêtes HTTP.
  - `models/`: Définitions des modèles de données.
  - `routes/`: Définitions des routes de l'API.
  - `middleware/`: Fonctions middleware personnalisées.
  - `services/`: Logique métier et interactions avec la base de données.
  - `utils/`: Fonctions utilitaires réutilisables.
  - `types/`: Définitions de types TypeScript personnalisés.
  - `server.ts`: Point d'entrée de l'application.

- `tests/`: Tests unitaires et d'intégration.
- `dist/`: Code compilé (généré automatiquement).
- `logs/`: Fichiers de logs.
- `.env`: Variables d'environnement (ne pas commiter).
- `.env.example`: Exemple de fichier .env (à commiter).
- `tsconfig.json`: Configuration TypeScript.

## Bonnes pratiques

1. **Séparation des préoccupations** : Chaque dossier a un rôle spécifique, ce qui facilite la maintenance et l'évolution du code.

2. **Modularité** : Organisez votre code en modules réutilisables.

3. **Nommage cohérent** : Utilisez une convention de nommage cohérente pour tous vos fichiers et dossiers.

4. **Évitez la duplication** : Utilisez des imports pour partager du code entre différents modules.

5. **Configuration centralisée** : Gardez toutes vos configurations dans le dossier `config/`.

6. **Gestion des erreurs centralisée** : Utilisez un middleware d'erreur global dans `middleware/errorHandler.ts`.

7. **Tests organisés** : Séparez les tests unitaires et d'intégration.

8. **Typage strict** : Utilisez TypeScript pour bénéficier d'un typage fort et améliorer la qualité du code.

En suivant cette structure et ces bonnes pratiques, vous aurez une base solide pour développer et faire évoluer votre application Express avec TypeScript.

Dans la prochaine section, nous allons voir comment créer notre serveur.

[Création du serveur](3_server-creation.md)
