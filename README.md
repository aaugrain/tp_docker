# TP 1 - Étude d'un processus dans un conteneur

Cet exercice étudie plus en détail le comportement d'un processus dans un conteneur.

***

1. Démarrez un conteneur docker à partir d'une image nginx en exposant le port 80 du conteneur vers le port 8000 de la machine hôte. Gardez le processus en premier plan.
    1. aller sur votre navigateur et taper l'URL

    ```html
    http://localhost:8000/
    ```

    Que voyez-vous apparaître sur votre console ou le processus docker tourne en premier plan?
    2. répétez l'opération avec l'URL suivante:

    ```html
    http://localhost:8000/error/
    ```

    Quelle nouvelle ligne voyez-vous apparaître sur la console?

    Remarque: 404 un code retour du protocole HTTP (sites web) qui précise que le serveur n'a pas trouvé l'élément demandé.
    3. Arrêtez le processus depuis votre console (Ctrl+C). Pouvez-vous toujours accéder au port 8000 depuis votre navigateur? Vérifier que le processus Docker est bien tombé à l'aide de le commande

    ```bash
    docker ps
    ```

    N.B: n'oubliez pas de rafraîchir votre navigateur si vous voyez encore une page Nginx.
    4. Supprimez le conteneur tombé à l'aide de la commande

    ```bash
    docker rm
    ```

2. Démarrez un nouveau conteneur Nginx mais en laissant le processus touner en tâche de fond cette fois.
    1. Vérifiez que vous avez de nouveau accès au port 8000 sur votre navigateur (n'oubliez pas de rafraîchir le cache si besoin).
    2. Utilisez la commande

    ```bash
    docker attach
    ```

    pour faire apparaître les logs du serveur Nginx sur vote console. Répéter les appels d'URL précédents pour faire apparaître de nouvelles lignes de logs.
    3. Si vous quitter (Ctrl+C), le processus Docker reste-t-il en vie?

3. Redémarrez le conteneur Nginx précédemment utilisé avec la commande
    1. Entrer dans le namespace du conteneur avec la commande

    ```bash
    docker exec
    ```

    Que voyez-vous comme invite de commande (PS1)? Est-ce celle de votre machine ou du namespace du conteneur?
    2. Chercher le fichier index.html dans le répertoire

    ```bash
    /usr/share/nginx/html
    ```

    et essayer de le modifier. Pourquoi ne trouvez-vous pas d'éditeur en ligne dans le conteneur? Afficher de nouveau la page d'accueil sur votre navigateur. A-t-elle été modifiée?
    3. Afficher le statut du service Nginx à l'aide de la commande

    ```bash
    service
    ```

    puis stopper le processus Nginx à l'aide de la même commande. Qu'observez-vous?

4. Redémarrez une dernière fois le conteneur Nginx et vérifier que la modification apporter au fichier index.html a été conservé. Que ce serait-il passé si vous aviez choisi de recréer un nouveau conteneur à la place?

5. Lors de la commande

```bash
docker attach
```

pourquoi le docker engine s'est-il directement branché sur les logs du serveur Nginx? Conclure sur la différence entre attach et exec pour interagir avec un processus Docker.
***
