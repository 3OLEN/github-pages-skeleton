# 3OLEN - GitHub Pages Skeleton

Modèle de base pour l'utilisation de GitHub Pages dans le cadre de sujets pour les
<abbr title="ORT LYON Enseignement Numérique">3OLEN</abbr>.

## 📦️ Composants

- Utilisation des dépendances supportées par [GitHub Pages](https://pages.github.com/versions/).
  - [Jekyll](https://jekyllrb.com/) v3.9<br>
    *Pour utiliser une version plus récente, il est nécessaire de définir une `GitHub Action` spécifique.*
  - [Minima](https://github.com/jekyll/minima) v2.5 (thème `light` + `dark` ; choix utilisateur via "footer")

# 📤️ Récupération du modèle

1. Récupération des sources depuis le dépôt GitHub : téléchargement des sources ou `git clone`.
2. Suppression du `.git` (si récupération par `git clone`).
3. Initialisation d'un nouveau dépôt Git : `git init --initial-branch main`.
4. Adaptation des fichiers pour le nouveau projet ; [Procédure détaillée](#-adaptions-des-fichiers).
5. Définition du dépôt GitHub : `git remote add origin <url_repository>`.
6. `git add . && git commit -m "🎉 New GitHub Pages project" && git push -u origin main`.

## ♻️ Adaptions des fichiers

Puisque les sources sont copiées, il est nécessaire d'adapter les différents fichiers pour la cohérence avec le nouveau
projet.

### 🐋 Docker

Tout ce qui se trouve dans les dossiers `bin/dev` et `docker` est lié à l'utilisation de docker afin de définir le
site en local et pouvoir le concevoir et le tester sans avoir besoin d'installer l'environnement GitHub Pages sur la
machine ni de le déployer à chaque modification sur GitHub.

#### « J'utilise Docker. »

Si vous comptez utiliser Docker, il est nécessaire de modifier le fichier [_parameters](bin/dev/_parameters) et les
variables :
- `DOCKER_IMAGE_NAME` : Nom de l'image Docker ; à modifier selon le nom du projet.
- `DOCKER_CONTAINER_NAME` : Nom du container Docker ; n'est peut-être pas à modifier.

Le détail de l'utilisation de Docker est défini à la section [Scripts Docker](#-scripts-utiles).

#### « Je n'utilise pas Docker. »

Si vous ne comptez pas utiliser Docker, vous pouvez supprimer ces dossiers.

Pour tester le site en local sans utiliser Docker, il sera nécessaire d'installer :
- [Ruby](https://www.ruby-lang.org/fr/) [>=2.5.0]
- [RubyGems](https://rubygems.org/)
- [Bundler](https://bundler.io/) (version 2.0 ou supérieure).

Puis d'exécuter les mêmes commandes que celles définies dans le fichier [entrypoint](docker/jekyll/entrypoint).

Source : [GitHub Pages - Testing your GitHub Pages site locally with Jekyll](https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll/testing-your-github-pages-site-locally-with-jekyll)

### 📝 README.md

L'ensemble du contenu du fichier `README.md` est à supprimer et à réécrire selon le nouveau projet.

### 🔧 Configuration

La configuration de Jekyll se trouve dans le fichier [_config.yaml](docs/_config.yaml) ; deux variables sont à
modifier :
- `title` : titre du site/projet ; est utilisée dans le `<title>` HTML.
- `description` : description du site/projet.

### 🍱 Site

La page d'accueil ([index.html](docs/index.html)) reprend seulement la description du site/projet. Vous pouvez la
modifier avant le commit initial ou le faire plus tard.

# Description et utilisation du modèle

## 💻️ Développement local

Les informations concernant le développement local (avec ou sans Docker) sont définies [plus haut](#-docker).

### 🔨 Scripts utiles

- `bin/dev/start`
  - Initialise l'environnement Docker en créant l'image utilisée par le container.
  - Crée un container en "one-shot" en se basant sur le `entrypoint`.
- `bin/dev/build`
  - Exécute la commande `jekyll build` (par le biais de `bundler`) dans le container Docker.
  - Il est parfois nécessaire de forcer un *build* pour que les modifications soient prises en compte, notamment sur
    la config, le style ou encore le templating dynamique.


## 🧱 Contenu du site

### 📄 Pages

Les pages sont définies à la racine des sources du site (dossier `docs`) ou dans des sous-dossiers, selon la
structuration prévue. Ces pages doivent utiliser l'extension `.html` ou `.md`.

> ⚠️ Le Front Matter est obligatoire pour que ces fichiers soient pris en compte par Jekyll.

La configuration de l'IDE doit être adaptée pour pouvoir associer ces fichiers au langage `Liquid` pour la coloration
syntaxique et l'autocomplétion.

La suite « Jetbrains » possède un plugin `Liquid`.

### 🍱 Templates réutilisables

Les `_layouts` ou les `_includes` peuvent être définis en tant que fichier `.liquid` (ou `.html.liquid` / `.md.liquid`)
afin d'utiliser la coloration syntaxique et l'autocomplétion pour `Liquid` de l'IDE.

# You better work! 🎶

Il ne reste plus qu'à vous mettre au travail et fournir un site "statique" selon vos besoins !

## 🔗 liens utiles

- [Documentation Jekyll](https://jekyllrb.com/docs/)
- [Documentation Liquid](https://shopify.github.io/liquid/)
- [Exemple du Projet 31](https://github.com/3OLEN/projet-31)
