---
title: "Nextcloud : La solution ultime pour remplacer Google Drive et autres"
date: 2023-09-30T20:00:00+01:00
description: Beaucoup d'entre nous se sont tournés vers des géants comme Google, mais vous êtes-vous déjà demandé s'il n'existait pas un meilleur moyen de gérer vos données personnelles sans compromettre votre vie privée ?
menu:
  sidebar:
    name: Private Cloud Drive
    identifier: nextcloud
    parent: raspberry
    weight: 10
---

À l'ère du numérique, le besoin de solutions de stockage sécurisées n'a jamais été aussi grand.

Beaucoup d'entre nous se sont tournés vers des géants comme Google Drive ou Microsoft OneDrive pour leur commodité et leur accessibilité.
Cependant, vous êtes-vous déjà demandé s'il n'existait pas un meilleur moyen de gérer vos données personnelles sans compromettre votre vie privée et votre flexibilité ?

Dans cet article, nous allons voir pourquoi Nextcloud est l'alternative idéale pour remplacer n'importe quel fournisseur de disque.

## Pourquoi utiliser des solutions comme Google Drive ou Microsoft OneDrive ?

Des services tels que Google Drive et Microsoft OneDrive offrent une facilité d'utilisation inégalée lorsqu'il s'agit de synchroniser des fichiers sur plusieurs appareils. Cette fonctionnalité garantit que vos documents, photos et autres fichiers sont toujours à jour et accessibles, ce qui est particulièrement précieux pour les utilisateurs qui ont besoin d'un accès en temps réel à leurs données.

Mais... Stocker vos données auprès de grandes entreprises signifie potentiellement compromettre votre vie privée, car elles peuvent accéder à vos informations personnelles et les utiliser. Cette question est devenue de plus en plus importante, en particulier dans le sillage des réglementations sur la vie privée telles que le Règlement général sur la protection des données (RGPD).

Ces dernières années, Google a fait l'objet d'actions en justice liées à ses règles d'utilisation des données. Par exemple, l'autorité française de protection des données, la CNIL, a infligé une amende importante à Google pour avoir enfreint le règlement RGPD, notamment en raison de l'insuffisance des informations fournies aux utilisateurs et de l'absence de consentement valide pour les publicités personnalisées. Cette condamnation souligne les graves préoccupations que suscite la manière dont Google traite les données des utilisateurs.

Avantages :
- **Pratique** : Des services comme Google Drive et Microsoft OneDrive offrent une synchronisation transparente entre les appareils, ce qui facilite l'accès à vos fichiers où que vous soyez.
- **Collaboration** : Ils offrent des fonctions de collaboration, telles que l'édition et le partage de documents en temps réel, qui sont essentielles pour le travail d'équipe.
- **Intégration** : L'intégration avec d'autres logiciels et services, tels que Google Workspace et Microsoft Office, peut améliorer la productivité.

Inconvénients :
- **Respect de la vie privée** : Le stockage de vos données auprès de grandes entreprises peut compromettre votre vie privée, car elles peuvent accéder à vos informations personnelles et les utiliser.
- **Personnalisation limitée** : Ces services manquent souvent d'options de personnalisation avancées pour les utilisateurs qui souhaitent avoir plus de contrôle sur leurs données.
- **Dépendance** : Le fait de dépendre d'un seul fournisseur vous rend vulnérable aux pannes de service et aux changements de conditions de service ou de prix.

## Utiliser son propre lecteur

Créer sa propre solution de stockage dans le Cloud peut sembler une tâche ardue, mais c'est une entreprise incroyablement excitante qui offre une pléthore d'avantages. 

Tout d'abord, vous êtes aux commandes, ce qui vous permet de contrôler totalement vos données et votre vie privée. L'intérêt réside dans la liberté de personnaliser votre Cloud en fonction de vos besoins exacts, qu'il s'agisse d'augmenter la capacité de stockage, de mettre en œuvre des mesures de sécurité avancées ou d'intégrer des fonctionnalités uniques. Ce qui rend ce voyage encore plus passionnant, c'est la passionnante communauté open-source qui entoure les solutions auto-hébergées comme Nextcloud.

Avec un réseau mondial de développeurs enthousiastes, ces communautés repoussent constamment les limites du possible. Elles améliorent et affinent les fonctionnalités, renforcent la sécurité et offrent un soutien inestimable. Alors, si vous êtes un bricoleur du web ou quelqu'un qui aime le plaisir de construire et de contribuer, je vous invite à plonger dans le monde des solutions auto-hébergées et à rejoindre ces projets open-source. **Quel que soit votre niveau de compétence, il y a une place pour tout le monde**, et votre participation peut faire une réelle différence pour façonner l'avenir des projets décentralisés, sécurisés et personnalisables.

Avantages :
- **Contrôle de la confidentialité** : L'hébergement de vos données sur votre propre infrastructure vous assure un contrôle total sur vos données et sur les personnes qui peuvent y accéder.
- **Économies** : Au fil du temps, l'hébergement de votre propre solution de stockage dans le nuage peut s'avérer rentable par rapport aux services par abonnement.
- **Personnalisation** : Vous pouvez adapter votre solution de stockage à vos besoins spécifiques, notamment en ce qui concerne les mesures de sécurité et la capacité de stockage.

Inconvénients :
- **Connaissances techniques** : La mise en place et la maintenance de votre propre solution de stockage dans le Cloud peuvent être décourageantes pour ceux qui n'ont pas d'expertise technique.
- **Investissement initial** : Il peut y avoir un coût initial pour le matériel et les logiciels, tels qu'un dispositif de stockage en réseau (NAS) et l'hébergement d'un serveur.
- **Responsabilité** : Vous êtes responsable des sauvegardes de données, de la sécurité et des mises à jour du système, ce qui peut prendre beaucoup de temps.

## NextCloud 

{{<img src="/posts/raspberry/nextcloud/nextcloud.webp" align="center" >}}

[NextCloud](https://nextcloud.com/) est une plateforme de collaboration et de stockage dans le Cloud auto-hébergée et open-source qui combine le meilleur des deux mondes.
Elle offre la commodité d'une synchronisation de fichiers et d'outils de collaboration basés sur le cloud, tout en vous permettant de garder le contrôle de vos données.

Caractéristiques principales de Nextcloud :

- **Stockage de fichiers** : Stockez, organisez et accédez facilement à vos fichiers depuis n'importe quel appareil.
- **Collaboration** : Partagez des fichiers, des calendriers, des contacts et hébergez même des appels vidéo au sein de votre instance Nextcloud.
- **Sécurité** : Nextcloud met l'accent sur la sécurité, en offrant des fonctionnalités telles que le chiffrement de bout en bout.
- **Personnalisation** : Vous pouvez étendre les fonctionnalités de Nextcloud grâce à une vaste sélection d'applications et de plugins.
- **Auto-hébergement** : Vous avez la propriété et le contrôle complets de vos données, ce qui garantit la protection de votre vie privée.

## Comment installer Nextcloud avec Docker

L'installation de Nextcloud avec Docker offre une solution flexible et personnalisable.
Docker vous permet d'encapsuler Nextcloud et ses dépendances dans des conteneurs, ce qui facilite l'installation et la gestion.

### Prérequis

Assurez-vous de disposez d'un serveur ou d'un périphérique NAS capable d'exécuter Docker.
Installer Docker sur votre serveur ou NAS. Suivre la documentation officielle de Docker pour votre plateforme.

### Docker

L'utilisation de l'image Docker de [LinuxServer](https://www.linuxserver.io/) est un choix prudent lorsque l'on envisage des solutions d'auto-hébergement comme Nextcloud, car elle introduit des fonctions de sécurité cruciales qui renforcent vos efforts de protection des données. L'une de ces fonctionnalités est l'implémentation de PUID (Process User ID) et PGID (Process Group ID), qui vous permet de contrôler précisément qui a les permissions de lecture et d'écriture sur votre système. Ce contrôle fin garantit que seuls les utilisateurs ou processus autorisés peuvent accéder à des fichiers ou répertoires spécifiques et les modifier, ce qui réduit le risque d'accès non autorisé ou de violation des données. En outre, la création d'un groupe Linux dédié avec des autorisations minimales renforce encore la posture de sécurité de votre système, en limitant les vulnérabilités potentielles.

De plus, l'image Docker de LinuxServer va encore plus loin en fournissant des MODS (Modular Object Detection System), une couche supplémentaire qui dote votre environnement auto-hébergé d'une série d'outils et de capacités étendues. Ces outils peuvent améliorer la fonctionnalité, la sécurité et les capacités de surveillance de votre solution de stockage.

La structure de dossier suivie permet une mise en place claire et organisée :

Dans le répertoire "nextcloud", vous avez segmenté vos composants en sous-répertoires distincts, ce qui facilite la gestion.

- Le répertoire "maria_db" abrite la base de données MariaDB sur laquelle Nextcloud s'appuie pour stocker les données et les configurations des utilisateurs en toute sécurité. La séparation de ce composant garantit l'isolation des données et une gestion efficace de la base de données.
- Le répertoire "nextcloud_config" est l'endroit où vous stockez vos fichiers de configuration Nextcloud, ce qui facilite l'accès et la modification des paramètres Nextcloud en cas de besoin.

Dans l'ensemble, cette structure de dossiers organisée et cette configuration démontrent une approche réfléchie de la création et de la maintenance d'une instance Nextcloud auto-hébergée robuste et sécurisée sur votre NAS.

```
nas/
├─ nextcloud/
│  ├─ maria_db/
│  ├─ nextcloud_config/
│  ├─ docker-compose.yml
│  ├─ .env
```

Le fichier "**docker-compose.yml**" est une pièce maîtresse du puzzle, car il orchestre l'ensemble de l'environnement Nextcloud à l'aide de conteneurs Docker. Ce fichier définit comment Nextcloud, MariaDB et tout autre service requis interagissent, simplifiant ainsi le déploiement et la maintenance.

```yml
version: '3.8'

services:
  nextcloud_db:
    image: lscr.io/linuxserver/mariadb:latest
    container_name: nextcloud_db
    restart: unless-stopped
    volumes:
      - ./maria_db:/config
    environment:
      - PUID=1000
      - PGID=100
      - TZ=Etc/UTC
      - MYSQL_ROOT_PASSWORD=$NEXTCLOUD_MYSQL_ROOT_PASSWORD
      - MYSQL_DATABASE=$NEXTCLOUD_MYSQL_DATABASE
      - MYSQL_USER=$NEXTCLOUD_MYSQL_USER
      - MYSQL_PASSWORD=$NEXTCLOUD_MYSQL_PASSWORD

  nextcloud_app:
    image: lscr.io/linuxserver/nextcloud:latest
    restart: unless-stopped
    ports:
      - 8443:443 # Replace 8443 by your custom exposed port
    depends_on:
      nextcloud_db:
        condition: service_started
    volumes:
      - ./nextcloud_config:/config
      - /volume1/cloud:/data # Replace /volume1/cloud to your local cloud path
    environment:
      - PUID=1000
      - PGID=100
      - TZ=Etc/UTC
      - DOCKER_MODS=linuxserver/mods:nextcloud-memories|linuxserver/mods:nextcloud-mediadc
      - MYSQL_HOST=nextcloud_db
      - MYSQL_DATABASE=$NEXTCLOUD_MYSQL_DATABASE
      - MYSQL_USER=$NEXTCLOUD_MYSQL_USER
      - MYSQL_PASSWORD=$NEXTCLOUD_MYSQL_PASSWORD
```

Le fichier "**.env**" contient des variables d'environnement nécessaires à la configuration de vos conteneurs Nextcloud et MariaDB, ce qui simplifie le processus d'installation.

```ini
NEXTCLOUD_MYSQL_DATABASE=nextcloud
NEXTCLOUD_MYSQL_USER=nextcloud
NEXTCLOUD_MYSQL_ROOT_PASSWORD=****************************
NEXTCLOUD_MYSQL_PASSWORD=****************************
```

### Run

```sh
docker-compose up -d
```

### Sécuriser votre instance

En utilisant efficacement `chmod`, `chown`, et en configurant `PUID` et `PGID` dans votre fichier Docker Compose, vous pouvez maintenir un environnement sécurisé et personnalisé pour vos services auto-hébergés tout en vous assurant que les permissions s'alignent sur les exigences de votre système.

Je recommande d'établir un groupe `docker` sur votre serveur et d'assigner un utilisateur unique pour chaque application hébergée dans ce groupe `docker`. Utilisez la commande `chown` de manière récursive pour accorder les permissions exclusivement à chaque utilisateur respectif. Dans l'éventualité d'une faille de sécurité, cette approche confine chaque application dans son espace désigné, atténuant ainsi les problèmes potentiels.

En outre, vous avez la possibilité de configurer les autorisations de manière plus granulaire, par exemple en accordant des autorisations complètes à l'utilisateur, un accès en lecture seule au groupe et aucun accès aux autres, ce qui renforce les mesures de sécurité.

Mettez en œuvre les meilleures pratiques de sécurité, telles que l'activation de HTTPS avec [Let's Encrypt](https://letsencrypt.org/fr/) et la configuration des autorisations des utilisateurs.

La plupart des solutions NAS offrent une fonction précieuse connue sous le nom de reverse proxy avec des certificats SSL/TLS [Let's Encrypt](https://letsencrypt.org/fr/). Cette fonctionnalité est généralement incluse dans le portail de configuration du NAS, ce qui simplifie le processus de sécurisation des applications et services web hébergés sur le NAS.

Si vous n'avez pas configuré de reverse proxy sur votre serveur, une autre excellente option consiste à utiliser [Nginx Proxy Manager](https://github.com/NginxProxyManager/nginx-proxy-manager), une solution open-source notable qui offre une alternative intéressante. Ce projet est réputé pour son approche conviviale et sa documentation simple et compréhensible. En outre, Nginx Proxy Manager peut être installé sans effort à l'aide de Docker, ce qui en fait un choix pratique pour ceux qui recherchent un moyen sans tracas de mettre en œuvre un proxy pour leurs services.

## Conclusion

Nextcloud offre une excellente alternative aux fournisseurs commerciaux de stockage cloud tels que Google Drive ou Microsoft OneDrive.

En auto-hébergeant NextCloud avec Docker, vous obtenez un contrôle total sur la confidentialité et la flexibilité de vos données tout en profitant des avantages d'une plateforme moderne de collaboration.

Faites le saut dans le monde de Nextcloud, et vous ne regarderez plus jamais les fournisseurs cloud traditionnels de la même façon.
