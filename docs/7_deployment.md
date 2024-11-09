# Déploiement

Cette section couvre les étapes nécessaires pour préparer et déployer votre application Express TypeScript en production.

## Préparation de l'application pour la production

1. **Compilation TypeScript** : Assurez-vous que votre code TypeScript est compilé en JavaScript. Utilisez la commande :
   ```bash
   npm run build
   ```

2. **Variables d'environnement** : Utilisez des variables d'environnement pour les configurations sensibles ou spécifiques à l'environnement. Vous pouvez utiliser le package `dotenv` pour gérer ces variables.

3. **Logging** : Implémentez un système de logging robuste. Winston est une bonne option pour Node.js.

4. **Gestion des erreurs** : Assurez-vous d'avoir une gestion d'erreurs appropriée en place.

5. **CORS** : Si votre API sera consommée par un front-end hébergé sur un domaine différent, configurez CORS correctement.

## Options de déploiement

### 1. Heroku

Heroku est une plateforme cloud qui simplifie le déploiement.

1. Créez un compte sur Heroku et installez l'Heroku CLI.
2. Initialisez un repo git si ce n'est pas déjà fait :

   ```bash
   git init
   ```
3. Créez une nouvelle application Heroku :

   ```bash
   heroku create
   ```
4. Ajoutez un fichier `Procfile` à la racine de votre projet avec le contenu :
   ```
   web: node dist/server.js
   ```
5. Poussez votre code vers Heroku :
   ```bash
   git push heroku main
   ```

### 2. DigitalOcean

DigitalOcean offre des Droplets (VPS) sur lesquels vous pouvez déployer manuellement.

1. Créez un Droplet sur DigitalOcean.
2. Connectez-vous via SSH.
3. Installez Node.js et npm.
4. Clonez votre repo git.
5. Installez les dépendances et construisez l'application.
6. Utilisez PM2 pour gérer votre processus Node.js :

   ```bash
   npm install -g pm2
   pm2 start dist/server.js
   ```

### 3. AWS Elastic Beanstalk

AWS Elastic Beanstalk gère le déploiement, de la mise à l'échelle à la surveillance de l'application.

1. Créez une application Elastic Beanstalk via la console AWS.
2. Configurez votre environnement (choisissez Node.js comme plateforme).
3. Déployez votre application en téléchargeant un bundle zip de votre code ou en connectant à votre repo git.

## Bonnes pratiques de déploiement

1. **Utilisez un gestionnaire de processus** : PM2 ou Forever pour garder votre application en cours d'exécution.

2. **Mettez en place un reverse proxy** : Utilisez Nginx comme reverse proxy devant votre application Node.js.

3. **Sécurité** : 
   - Utilisez HTTPS
   - Implémentez une protection contre les attaques DoS/DDoS
   - Gardez vos dépendances à jour

4. **Monitoring** : Mettez en place des outils de monitoring comme New Relic ou Datadog.

5. **Mise à l'échelle** : Préparez votre application pour la mise à l'échelle horizontale si nécessaire.

6. **Sauvegarde** : Mettez en place des sauvegardes régulières de vos données.

7. **CI/CD** : Utilisez des outils d'intégration continue et de déploiement continu comme Jenkins, GitLab CI, ou GitHub Actions.

En suivant ces étapes et bonnes pratiques, vous serez en mesure de déployer efficacement votre application Express TypeScript en production.

-----------
Retour à la 
[page d'accueil](index.md) |  [dépot Github](https://github.com/NCherfaoui/express-typescript-tutorial/)
