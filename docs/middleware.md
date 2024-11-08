# Utilisation des middleware

Les middleware sont des fonctions qui ont accès à l'objet de requête (req), l'objet de réponse (res), et la fonction middleware suivante dans le cycle requête-réponse de l'application (généralement appelée next).

## Qu'est-ce qu'un middleware ?

Les middleware peuvent :
- Exécuter n'importe quel code
- Apporter des modifications aux objets de requête et de réponse
- Terminer le cycle requête-réponse
- Appeler le prochain middleware dans la pile

## Middleware intégrés d'Express

Express dispose de plusieurs middleware intégrés que vous pouvez utiliser directement :

```typescript
import express from 'express';

const app = express();

// Pour parser le corps des requêtes JSON
app.use(express.json());

// Pour parser le corps des requêtes URL-encoded
app.use(express.urlencoded({ extended: true }));

// Pour servir des fichiers statiques
app.use(express.static('public'));
```

## Création de middleware personnalisés

Vous pouvez créer vos propres middleware. Voici un exemple de middleware qui enregistre les détails de chaque requête :

```typescript
import { Request, Response, NextFunction } from 'express';

const loggerMiddleware = (req: Request, res: Response, next: NextFunction) => {
  console.log(`${new Date().toISOString()} - ${req.method} ${req.path}`);
  next();
};

app.use(loggerMiddleware);
```

## Middleware d'erreur

Les middleware d'erreur sont définis avec quatre arguments au lieu de trois :

```typescript
app.use((err: Error, req: Request, res: Response, next: NextFunction) => {
  console.error(err.stack);
  res.status(500).send('Something broke!');
});
```

## Middleware pour des routes spécifiques

Vous pouvez appliquer un middleware à une route spécifique :

```typescript
const authMiddleware = (req: Request, res: Response, next: NextFunction) => {
  // Vérifiez l'authentification ici
  if (/* l'utilisateur est authentifié */) {
    next();
  } else {
    res.status(401).send('Unauthorized');
  }
};

app.get('/protected', authMiddleware, (req: Request, res: Response) => {
  res.send('This is a protected route');
});
```

## Chaînage de middleware

Vous pouvez chaîner plusieurs middleware pour une route :

```typescript
app.get('/complex', 
  firstMiddleware, 
  secondMiddleware, 
  (req: Request, res: Response) => {
    res.send('This route uses multiple middleware');
  }
);
```

Dans la prochaine section, nous aborderons les tests de notre application Express.
