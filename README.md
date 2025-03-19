# Installation

## VSCode
- Installer l'extension Vue

# Développement

## Installation des dépendances
- `docker exec dev-vue-cars npm install`

## Démarrer le serveur (A faire à chaque fois)
- Démarrer le conteneur Docker : `docker-compose up -d`
- Se connecter au conteneur web : `docker exec -it vue_intro bash`


## Pour développer avec Vue
- Une fois dans le conteneur web
- Aller dans le dossier du projet : `cd <nom_du_projet>`
- Initialiser le projet : `npm install`
- Démarrer le serveur avec le mode de watch : `npm run dev`
- Accéder au site : `http://localhost:8000/`


# TODO
- [ ] Problème d'affichage, le contenu dépasse de la page
- [ ] Ne pas ajouter d’éléments si le champ est vide
- [ ] Afficher un bord rouge si le champ est vide lors de l'appui sur le bouton (classe input-error)
- [ ] Problème d'ajout d’éléments dans la liste
- [ ] Plusieurs éléments sont supprimés lors de l'appui sur le bouton
- [ ] Les voitures sont ajoutées dans le mauvais ordre par rapport à la liste JS
- [ ] Utiliser la classe selected pour mettre en surbrillance l'élément sélectionné
- [ ] Il y a un problème lors de la sélection, le détail ne s'affiche pas
- [ ] La hauteur de la zone détail doit être de 200px
- [ ] Les coins de la zone détail doivent être arrondis