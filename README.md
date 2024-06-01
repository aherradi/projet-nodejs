Nous nous proposons de développer un Blog dont les parties Backend et Frontend seront développées et testées séparément. Le backend fonctionne sous forme d’API JSON. Voici les technologies qui seront adoptées pour ce projet :
Du côté backend :
le framework NodeJS Express pour le serveur Web
l’ORM Prisma et une base de données Mysql/MariaDB pour la persistance de données
Du côté frontend :
Libre


B - CONTRAINTES FONCTIONNELLES
L’application Blog devra gérer quatre entités :
Utilisateur :
nom, 
email, 
password, 
role qui doit être un parmi (ADMIN, AUTHOR)
Article 
titre, 
contenu, 
image, 
createdAt,  (date)
updatedAt, (date)
published (Boolean)
Categorie 
nom
Commentaire 
email,
contenu

Relations entre les entités :
Un article est associé à un et un seul utilisateur (Cet utilisateur devrait avoir le role AUTHOR)
Un utilisateur (ayant le rôle AUTHOR) peut écrire zéro ou plusieurs articles
Un article est associé à zéro ou plusieurs catégories
Une catégorie est associée à zéro ou plusieurs articles
Un commentaire est associé à exactement un article
Un article est associé à zéro ou plusieurs commentaires.


Créer un projet dans VS Code dans un dossier  nommé projet-web.
Initiez le suivi du projet à l’aide de git (git init), ajoutez un fichier README.md puis faites un premier commit. Synchronisez ensuite, votre projet avec le dépôt distant correspondant.
Initiez dans ce dossier, un projet Express en utilisant la commande “express” (si elle n’est pas installée allez voir ici). Puis installez les dépendances.
Ajoutez dans la racine du projet un fichier nommé “.gitignore” contenant “node_modules”. (Pour éviter d’envoyer ce dossier au dépôt distant)
Faites un GIT COMMIT, puis un  GIT PUSH
Dans le dossier routes, ajouter trois fichiers :
articles.js
categories.js
commentaires.js
Pour chacun des fichiers (articles.js, categories.js, commentaires.js et users.js), ajouter les routes permettant d’effectuer les opérations de base CRUD :
Articles (chemin de base /articles)
Méthode HTTP
Path
Paramètres d’URL
Commentaire
GET
/
take, skip
Récupérer take articles à partir de la position skip.
take (nombre d’éléments)
skip (offset à partir de laquelle on extrait les données de la base)
GET
/:id


Récupérer un article ayant l’id donné
POST
/


Ajouter un nouveau article envoyé sous format JSON
PATCH
/


Mettre à jour l’article envoyé dans le corps de la requête.
DELETE
/:id


Supprimer l’article ayant l’id donné.


Suivre le même modèle pour les autres routes.
Pour tester les routes, créer un dossier test et mettez dedans les fichiers suivants :
articles.http
categories.http
commentaires.http
users.http
Ces fichiers sont associés à l’extension VS Code “REST Client” qui nous permettra d’écrire et d’exécuter les requêtes directement à partir de VS Code.

Faites un GIT COMMIT puis un GIT PUSH
Installez la CLI Prisma et le Client Prisma
> npm i -D prisma
> npm i @prisma/client
Initiez un dans la racine de votre projet la prise en charge de l’ORM Prisma :
> npx prisma init
Dans le fichier “.env”, configurer l’utilisation d’un SGBBR MySQL/MariaDB. Assurez-vous d’avoir un serveur MySQL/MariaDB démarré.
Ajouter dans le fichier “prisma/schema.prisma”, les modèles reflétant les entités et les relations entre elles. Compléter la configuration pour la prise en charge de mysql.
Effectuez les migrations puis régénérer le client Prisma (migrate/generate) et enfin vérifier en ouvrant prisma studio. (> npx prisma studio) puis tester en ajoutant des données à l’aide studio.
