# Création du serveur

Dans cette section, nous allons créer un serveur Express de base en utilisant TypeScript.

## Création du fichier server.ts

Dans le dossier `src`, créez un fichier `server.ts` avec le contenu suivant :

```typescript
import express, { Express, Request, Response } from 'express';

const app: Express = express();
const port = process.env.PORT || 3000;

app.get('/', (req: Request, res: Response) => {
  res.send('Hello World from Express + TypeScript!');
});

app.listen(port, () => {
  console.log(`Server running at http://localhost:${port}`);
});
```

## Explication du code

1. Nous importons `express` et les types nécessaires depuis le module '@types/express'.
2. Nous créons une instance de l'application Express.
3. Nous définissons le port sur lequel le serveur écoutera (utilisant une variable d'environnement ou 3000 par défaut).
4. Nous définissons une route GET pour la racine ('/') qui renvoie un message "Hello World".
5. Enfin, nous démarrons le serveur en écoutant sur le port spécifié.

## Exécution du serveur

Pour exécuter le serveur en mode développement, utilisez la commande :

```bash
npm run dev
```

Vous devriez voir le message "Server running at http://localhost:3000" dans la console.

## Test du serveur

Ouvrez votre navigateur et allez à `http://localhost:3000`. Vous devriez voir le message "Hello World from Express + TypeScript!".

Dans la prochaine section, nous explorerons comment définir des routes plus complexes dans notre application Express.

[Routes](4_routes.md)