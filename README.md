# Gardener pour Home Assistant OS — prototype d'app

Ce dépôt est un **prototype à tester**, pas une version officielle ni une version validée en production.

Il emballe l'application open source [mniedermaier/gardener](https://github.com/mniedermaier/gardener) dans une app Home Assistant. L'image est construite depuis les sources amont pendant la construction de l'app.

## Important
- Le dépôt amont évolue : pour une installation reproductible, remplacez `main` dans le Dockerfile par un tag ou un commit précis après validation.
- Cette version expose l'interface sur le port hôte `8099` (adresse : `http://IP_DE_HOME_ASSISTANT:8099`) au lieu d'utiliser Ingress. C'est intentionnel pour le prototype.
- Le build n'a pas été exécuté ni testé sur une instance Home Assistant réelle.
- Ne publiez pas ce service sur Internet sans ajouter une authentification et une configuration de sécurité adaptées.
- Les données SQLite doivent être persistées dans le dossier `/data` de l'app.
