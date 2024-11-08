# Définition des routes

Dans cette section, nous allons explorer comment définir et organiser les routes dans une application Express avec TypeScript.

## Structure des routes

Il est recommandé d'organiser vos routes dans des fichiers séparés pour une meilleure maintenabilité. Créez un dossier `routes` dans votre dossier `src` et ajoutez-y un fichier `index.ts`.

## Création d'un routeur

Dans `src/routes/index.ts`, créez un routeur Express :

```typescript
import express, { Router, Request, Response } from 'express';

const router: Router = express.Router();

router.get('/', (req: Request, res: Response) => {
  res.send('Hello from the root route!');
});

router.get('/about', (req: Request, res: Response) => {
  res.send('This is the about page.');
});

export default router;
```

## Intégration du routeur dans server.ts

Modifiez votre `src/server.ts` pour utiliser ce routeur :

```typescript
import express, { Express } from 'express';
import routes from './routes';

const app: Express = express();
const port = process.env.PORT || 3000;

app.use('/', routes);

app.listen(port, () => {
  console.log(`Server running at http://localhost:${port}`);
});
```

## Paramètres de route

Vous pouvez définir des routes avec des paramètres dynamiques. Par exemple :

```typescript
router.get('/users/:id', (req: Request, res: Response) => {
  const userId = req.params.id;
  res.send(`User ID: ${userId}`);
});
```

## Gestion des requêtes POST

Pour gérer les requêtes POST, vous devez d'abord ajouter un middleware pour parser le corps de la requête. Ajoutez ceci à votre `server.ts` :

```typescript
app.use(express.json());
```

Ensuite, vous pouvez définir une route POST :

```typescript
router.post('/users', (req: Request, res: Response) => {
  const { name, email } = req.body;
  // Ici, vous traiteriez normalement les données, par exemple en les sauvegardant dans une base de données
  res.status(201).json({ message: 'User created', user: { name, email } });
});
```

## Test des routes

Vous pouvez tester vos routes en utilisant des outils comme Postman ou curl. Par exemple :

```bash
curl http://localhost:3000/about
curl http://localhost:3000/users/123
curl -X POST -H "Content-Type: application/json" -d '{"name":"John","email":"john@example.com"}' http://localhost:3000/users
```

Dans la prochaine section, nous explorerons l'utilisation des middleware dans Express.
