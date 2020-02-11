# TP 3 - Étude de la notion de volume

## Objectif

Cet exercice étudie plus en détail comment monter un volume partagé entre un conteneur et la machine hôte.

***

1. Démarrez un conteneur docker à partir d'une image jenkins officielle en exposant le port 8080 du conteneur vers le port 80800 de la machine hôte et le port 50000 vers le port 50000.
   - aller sur votre navigateur et taper l'URL

   ```html
   http://localhost:8080/
   ```

   Et entrez dans le conteneur pour récupérer le mot de passe initial.

   - Poursuivez la configuration initiale de Jenkins.

   - Stoppez et supprimez le conteneur.

1. Lancez la commande

   ```bash
   docker volume ls
   ```

   Que voyez-vous apparaître?

   - Faites une recherche par nom de fichier à partir du numéro de volume indiqué. Où se trouve le volume?

   - Entrez dans le répertoire indiqué et affichez son contenu. Que voyez-vous?

1. Démarrez un nouveau conteneur Jenkins en ajoutant un flag pour monter un volume partagé entre le conteneur et la machine hôte avec le flag

   ```bash
   -v host_directory:container_directory
   ```

   - Allez chercher le secret initial dans votre volume partagé sans entrer dans le conteneur. Poursuivez avec la configuration de Jenkins et créez un premier job.

   - Stoppez et supprimez le conteneur jenkins. Assurez-vous que le volume partagé contient toujours les données de configurations.

   - Lancez un nouveau conteneur Jenkins en utilisant le même volume que précédemment. Qu'observez-vous lors du démarrage? Retrouvez-vous le job précédemment créé?

1. Conclure sur l'utilité des volumes dans les conteneurs.

1. Que signifie "stateless" et "stateful" en informatique?

***
