# Tests

Les tests sont une partie cruciale du développement logiciel. Dans cette section, nous allons explorer comment configurer et écrire des tests pour notre application Express avec TypeScript.

## Configuration de l'environnement de test

Nous utiliserons Jest comme framework de test. Commencez par installer les dépendances nécessaires :

```bash
npm install --save-dev jest ts-jest @types/jest supertest @types/supertest
```

Créez un fichier `jest.config.js` à la racine de votre projet :

```javascript
module.exports = {
  preset: 'ts-jest',
  testEnvironment: 'node',
  roots: ['<rootDir>/src'],
  testMatch: ['**/__tests__/**/*.ts', '**/?(*.)+(spec|test).ts'],
  transform: {
    '^.+\.ts$': 'ts-jest',
  },
};
```

Ajoutez un script de test à votre `package.json` :

```json
"scripts": {
  "test": "jest"
}
```

## Écriture de tests unitaires

Les tests unitaires se concentrent sur des parties isolées de votre code. Créez un dossier `__tests__` dans votre dossier `src` et ajoutez-y un fichier `example.test.ts` :

```typescript
describe('Example Test Suite', () => {
  it('should add two numbers correctly', () => {
    expect(1 + 2).toBe(3);
  });

  it('should concatenate strings', () => {
    expect('Hello' + ' ' + 'World').toBe('Hello World');
  });
});
```

## Écriture de tests d'intégration

Les tests d'intégration vérifient comment différentes parties de votre application fonctionnent ensemble. Nous utiliserons Supertest pour tester nos routes Express.

Créez un fichier `server.test.ts` dans le dossier `__tests__` :

```typescript
import request from 'supertest';
import express from 'express';
import router from '../routes';

const app = express();
app.use('/', router);

describe('Integration Tests', () => {
  it('should return 200 OK for GET /', async () => {
    const response = await request(app).get('/');
    expect(response.status).toBe(200);
    expect(response.text).toBe('Hello from the root route!');
  });

  it('should return 404 for undefined routes', async () => {
    const response = await request(app).get('/undefined-route');
    expect(response.status).toBe(404);
  });
});
```

## Exécution des tests

Pour exécuter vos tests, utilisez la commande :

```bash
npm test
```

## Bonnes pratiques de test

1. **Isolez vos tests** : Chaque test devrait être indépendant des autres.
2. **Nommez vos tests clairement** : Le nom du test devrait décrire ce qu'il teste.
3. **Testez les cas positifs et négatifs** : Assurez-vous de tester non seulement les scénarios de réussite, mais aussi les cas d'erreur.
4. **Utilisez des mocks quand c'est nécessaire** : Pour les dépendances externes comme les bases de données, utilisez des mocks pour isoler vos tests.
5. **Maintenez vos tests** : Mettez à jour vos tests en même temps que votre code.

Dans la prochaine section, nous aborderons le déploiement de notre application Express.
