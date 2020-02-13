# TP 4 - Déploiement à l'aide de docker compose

## Objectif

Cet exercice étudie plus en détail comment orchestrer des conteneurs à l'aide de docker compose.

### Les fichier docker-compose.yml

Le fichier yaml est le suivant:

```yaml
version: '3'
services:
  jenkins:
    image: jenkins/jenkins:lts
    ports:
      - "8080:8080"
    volumes:
      - jenkins_home:/var/jenkins_home
  gitlab:
    image: gitlab/gitlab-ce
    ports:
     - "80:80"
     - "443:443"
     - "2224:22"
    volumes:
     - gitlab_config:/etc/gitlab
     - gitlab_logs:/var/log/gitlab
     - gitlab_data:/var/opt/gitlab
  nexus:
    image: sonatype/nexus3
    ports:
     - "8081:8081"
    volumes:
     - nexus_data:/nexus-data
volumes:
 jenkins_home:
 gitlab_config:
 gitlab_logs:
 gitlab_data:
 nexus_data:
```

### Les services

Ils sont au nombre de trois:

1. Un serveur Gitlab (Community Edition)

   ```yaml
   gitlab:
    image: gitlab/gitlab-ce
    ports:
     - "80:80"
     - "443:443"
     - "2224:22"
    volumes:
     - gitlab_config:/etc/gitlab
     - gitlab_logs:/var/log/gitlab
     - gitlab_data:/var/opt/gitlab
   ```

1. Un serveur Jenkins

   ```yaml
   jenkins:
    image: jenkins/jenkins:lts
    ports:
      - "8080:8080"
    volumes:
      - jenkins_home:/var/jenkins_home
   ```

1. Un serveur Nexus

   ```yaml
   nexus:
    image: sonatype/nexus3
    ports:
     - "8081:8081"
    volumes:
     - nexus_data:/nexus-data
   ```

### Le réseau

Docker Compose gère les conteneurs via un DNS local:

- Gitlab est accessible depuis l'URL <http://gitlab/> ou <ssh://gitlab:2224/>

- Jenkins est accessible depuis l'URL <http://jenkins:8080/>

- Nexus est accessible dpuis l'URL <http://nexus:8081/>

### Les volumes

Il y en a 5 en tout.

- un pour les données Jenkins

- un pour la configuration de Gitlab

- un pour les logs de Gitlab

- un pour les données de Gitlab

- un dernier pour les données de Nexus

### Lancer les services

La commande:

```bash
docker-compose up -d
```

Pour supprimer les services

```bash
docker-compose down
```

Pour supprimer le contenu des volumes par la même occasion

```bash
docker-compose down --volumes
```

***
