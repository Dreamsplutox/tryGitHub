### Introduction : L'architecture que nous allons mettre en place
Pour qu'un Data warehouse soit utile à une entreprise, il faut que plusieurs autres outils soient installés et intéragissent avec ce dernier comme nous l'avons dans la première partie de ce cours.

Voici donc un petit rappel de ce que nous allons mettre en place : 

**IMAGE ARCHITECTURE DATA WAREHOUSE**

En l'occurrence, nous allons utiliser MySQL Workbench pour créer nos bases de données et installer les outils Pentaho qui permettent entre autres, de créer des rapports, les publier sur un serveur web et réaliser des traitements ETL sur les données.

### Partie I : Installation de la suite BI Pentaho
Dans le cadre du cours, nous n'utiliserons que 4 outils pentaho (report desginer, PDI, Pentaho server, Pentaho Schema Workbench)

Il y a donc 2 choix possibles pour l'installation : 
  - Installer uniquement ces 4 outils pour poursuivre le cours
  - Installer toute la suite Pentaho pour tester d'autres logiciels plus tard


#### Choix n°1
Se rendre sur ce site https://sourceforge.net/projects/pentaho/files/Pentaho%209.1,
aller dans la partie "server" et télécharger le zip **pentaho-server-ce-9.1.0.0-324.zip**

Retourner dans le dossier parent puis aller dans la partie "client-tools",
dans cette partie, il faut télécharger
  - **pdi-ce-9.1.0.0-324.zip**
  - **prd-ce-9.1.0.0-324.zip**
  - **psw-ce-9.1.0.0-324.zip**

Il ne vous reste plus qu'à dézipper l'ensemble des zip dans le même répertoire 

#### Choix n°2 
Télécharger Pentaho en utilisant ce script bash (s'il n'est plus à jour, allez sur le site de source forge et récupérez la version plus récente, dans notre cas ça sera Pentaho 9.1)

(Si vous n'avez pas wget, installez git bash et suivez les étapes présentes sur ce site pour obtenir wget https://www.codegrepper.com/code-examples/shell/wget+git+bash (mais ne pas renommer wget))

```bash
curl https://sourceforge.net/projects/pentaho/rss?path=/Pentaho%209.1 | grep "<link>.*</link>" | sed 's|<link>||;s|</link>||' | while read url; do url=`echo $url | sed 's|/download$||'`; wget $url ; done
```

### Partie II :  création + initialisation des bases de données (rapide, pour vidéo on pourra créer le schéma + remplir étape par étape)
- Installer un serveur MySQL + MySQL Workbench https://dev.mysql.com/downloads/installer/
IMAGE MYSQL SERVER

- Utiliser les scripts fournis en pièce jointe de cette page pour créer la base de données de la société :
	IMAGE_SCRIPTS
	- Créer base de données initiale dans MySQL Workbench en executant le script "create normal model for BtoBlogistics"
	- Alimenter BtoBlogistics avec le script "insert_data_for_basic_btob_model"

- Créer base de données en étoile en exécutant le script "create star model for BtoBlogistics" ==> **A NE PAS METTRE POUR LA PARTIE DEFINITION DES BESOINS**

### Partie III : Configuration minimale des outils que nous allons utiliser
Maintenant que les bases de données et les outils Pentaho sont installés, il va falloir les configurer. 

La première chose à faire est de télécharger un connecteur MySQL pour que nos outils puissent communiquer avec nos bases de données, voici le lien (https://dev.mysql.com/downloads/file/?id=496255)

Il va falloir ensuite se rendre dans le dossier où tout a été dézippé :
IMAGE_DOSSIER_DEZIP
 et compléter les étapes ci-dessous.

#### Installation de java JDK et JRE 1.8 + configuration des variables d'environnement
- Installer JDK (lien : https://www.oracle.com/java/technologies/javase/javase-jdk8-downloads.html)
- Installer JRE (lien : https://java.com/en/download/)
- Configuration des variables d'environnement PENTAHO_JAVA, PENTAHO_JAVA_HOME et JAVA_HOME
IMAGE_var_envi

#### Serveur Pentaho : Pentaho Business Analytics Server (**Si on utilise pentaho pour créer des rapports a la place de powerBI**)
##### 1) Déplacer le connecteur MySQL au bon endroit
##### 2) Démarrer le serveur
##### 3) Se connecter et ajouter une source de données **A NE PAS FAIRE DANS LA PARTIE I**

#### L'ETL de Pentaho : Pentaho Data Integration
##### 1) Déplacer le connecteur MySQL au bon endroit
##### 2) Démarrer l'application
##### 3) Relier l'application au serveur 
##### 4) Ajouter les sources de données **A NE PAS FAIRE DANS LA PARTIE I**

#### L'outil reporting de Pentaho : Pentaho Report Designer (**Si on utilise pentaho pour créer des rapports a la place de powerBI**)
##### 1) Déplacer le connecteur MySQL au bon endroit
##### 2) Démarrer l'application
##### 3) Relier l'application au serveur
##### 4) Ajouter les sources de données **A NE PAS FAIRE DANS LA PARTIE I**

#### Le concepteur de cubes mondrian : Pentaho Schema Workbench
##### 1) Déplacer le connecteur MySQL au bon endroit
##### 2) Démarrer l'application
##### 3) Relier l'application au serveur
##### 4) Ajouter les sources de données **A NE PAS FAIRE DANS LA PARTIE I**