# TP 2 - Étude des points de montage dans un conteneur

## Objectif

Cet exercice étudie plus en détail le montage des différents volumes dans le namespace d'un conteneur.

***

1. Démarrez un conteneur docker à partir d'une image bash. Gardez le processus en premier plan et en mode interactif avec un pseudo-terminal à disposition.

   - Une fois à l'intérieur du conteneur, afficher la liste des systèmes de fichiers montés à l'aide de la commande

   ```bash
   df
   ```

   Comparez avec les différents systèmes de fichiers de votre machine hôte.

   - Affichez plus de propriétés sur les systèmes de fichiers du conteneur en inspectant le fichier

   ```bash
   /proc/mounts
   ```

   Et comparez avec celui de votre machine hôte. Indiquez notamment quels sont ceux en read-only (ro) au lieu de read-write (rw). Pouvez-vous expliquer la raison de cette différence?

   - Modifier le fichier système

   ```bash
   /etc/sysctl.conf
   ```

   en essayant de modifier le nombre de fichier ouvrable en parralèle en ajoutant la ligne

   ```bash
   fs.file-max = 209708
   ```

   Vous pouvez normalement modifier la configuration du système à chaud à l'aide de la commande

   ```bash
   sysctl -p /etc/sysctl.conf
   ```

   Que se passe-t-il dans le conteneur si vous lancez cette commande? Pouvez-vous comparer avec votre machine hôte?

   - Stopper et détruiser le conteneur.

1. Démarrez un conteneur docker à partir d'une image bash. Gardez le processus en premier plan et en mode interactif avec un pseudo-terminal à disposition. Ajoutez cette fois le flag

   ```bash
   --privileged
   ```

   - Répétez les étapes de la première question et notez s'il y a des différences dans le conteneur.

   - Une fois appliquer la commande de reconfiguration du système à chaud quittez ET détruisez le conteneur. Afficher les propriétés systèmes de la machine hôte à l'aide de la commande

   ```bash
   sysctl -a
   ```

   et cherchez la configuration fs.file-max. Qu'observez-vous?

   - Essayez de modifier à nouveau le système de la machine hôte en utilisant un conteneur "privilégié".

1. Conclure sur la manière dont un conteneur utilise le système de la machine hôte. Comparez avec la virtualisation via une machine virtuelle et un hyperviseur.

***
