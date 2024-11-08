Conception d'une infrastructure AWS pour une application Docker révolutionnaire

Réalisé par : Yanis Zedira et Aymen Djerad
Contexte

Nous venons de terminer le développement de notre application révolutionnaire composée de deux images Docker : un backend et un frontend. Notre objectif est de déployer cette application sur AWS en utilisant une architecture serverless et managée. Cette infrastructure doit également être déployée sur deux zones de disponibilité pour garantir une haute disponibilité et une résilience face aux désastres naturels.
1. Sélection des composants AWS

Pour déployer notre application sur AWS, nous avons sélectionné les composants suivants :

    Elastic Container Service (ECS) avec Fargate : Un service managé permettant d'exécuter des conteneurs Docker sans gérer les serveurs sous-jacents. ECS avec Fargate offre une scalabilité automatique et simplifie la gestion des conteneurs​

​

.

Application Load Balancer (ALB) : Agit comme un reverse proxy pour répartir le trafic entre les instances de conteneurs déployées dans plusieurs zones de disponibilité (AZ). Le ALB permet d'assurer la haute disponibilité en redirigeant le trafic vers une zone fonctionnelle en cas de panne de l'autre​
​

.

Virtual Private Cloud (VPC) : Crée un environnement réseau isolé et sécurisé pour déployer les ressources AWS. Notre VPC sera divisé en sous-réseaux publics et privés pour optimiser la sécurité et l'accessibilité de l'application​

.

Amazon RDS (pour le backend) : Service de gestion de bases de données relationnelles, qui assure la sécurité et la disponibilité des données de notre application. Amazon RDS simplifie la gestion des bases de données sans avoir à gérer directement l'infrastructure sous-jacente.

Security Groups : Firewalls virtuels qui contrôlent le trafic entrant et sortant de nos ressources AWS. Les Security Groups vont limiter les accès à notre application en fonction de règles spécifiques, garantissant ainsi une sécurité accrue​

.

CloudFront : Réseau de diffusion de contenu (CDN) utilisé pour améliorer l'expérience utilisateur en servant les contenus statiques (comme les images) depuis des emplacements proches géographiquement des utilisateurs.

Amazon S3 : Fournit un stockage d'objets sécurisé et durable pour les fichiers statiques (images, documents) de notre application. S3 facilite la gestion des fichiers statiques, tout en étant facilement accessible et résistant​

    .

2. Schéma de l'infrastructure

Voici le schéma de l'infrastructure que nous avons conçue pour déployer notre application sur AWS :

![Description de l'image](C:/Users/pc/OneDrive/Bureau/tp%20docker/hetic-infra-2/tp1.png)

![Description de l'image](C:/Users/pc/OneDrive/Bureau/tp%20docker/hetic-infra-2/tp2.png)


3. Justification des choix techniques

ECS avec Fargate : Nous avons choisi ECS avec Fargate pour son architecture serverless, qui permet d'exécuter des conteneurs sans avoir à gérer l'infrastructure. Fargate ajuste automatiquement les ressources en fonction de la demande, ce qui évite des coûts inutiles. Cette solution est idéale pour une application évolutive et réduit la complexité de gestion des serveurs​

.

Application Load Balancer (ALB) : Le ALB assure un équilibrage de charge efficace et garantit la haute disponibilité. En cas de problème dans une zone de disponibilité, le ALB redirige le trafic vers une autre, maintenant ainsi l'application en ligne. De plus, le ALB permet de masquer l'IP des serveurs pour améliorer la sécurité de notre infrastructure​

.

VPC et Security Groups : La combinaison d'un VPC et de Security Groups permet de créer un réseau privé et sécurisé. Les Security Groups agissent comme des pare-feu virtuels et limitent les accès aux ressources de l'application en fonction des besoins de sécurité​

.

Amazon RDS : Pour notre backend, Amazon RDS gère les bases de données relationnelles de manière managée, offrant une haute disponibilité et des sauvegardes automatiques. Cela permet d'assurer la sécurité et la durabilité des données tout en nous évitant de gérer directement l'infrastructure​

.

CloudFront : Le CDN CloudFront optimise l'accès aux utilisateurs finaux en mettant en cache le contenu aux emplacements les plus proches des utilisateurs, ce qui réduit la latence et améliore l'expérience utilisateur.

Amazon S3 : S3 fournit un stockage fiable et accessible pour les fichiers statiques, comme les images. Cela simplifie la gestion des fichiers statiques tout en réduisant les coûts de stockage.
Bonus : Service AWS pour uploader les images Docker

Nous avons utilisé Amazon Elastic Container Registry (ECR) pour stocker et gérer les images Docker de notre application. ECR permet de stocker les images Docker de manière sécurisée et intégrée avec ECS, facilitant le déploiement de nos conteneurs sans complexité supplémentaire​
​.