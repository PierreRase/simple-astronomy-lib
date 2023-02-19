Pour ce TP d'intégration continue, je me suis basé sur un projet Git déjà existant, "simple-astronomy-lib" (https://github.com/SimpleAstronomy/simple-astronomy-lib)

Ce qui fonctionne : 

-build du code
-exécution des test unitaires
-génération et déploiement d'un package sur Nexus

Les étapes réalisées : 

-Récupération du projet github 
-Création du projet sur Jenkins
-Ajout des pluggins Maven et Nexus sur Jenkins
-Création d'un nouvel utilisateur Nexus : jenkins-user
-Ajout du 'crédential' jenkins-user sur Jenkins
-Modification de la pipeline pour effectuer le build, les tests et le stockage sur Nexus

Tentatives qui n'ont pas fonctionnées : 

J'ai voulu installer un serveur SonarQube, cependant le serveur n'a jamais voulu démarrer.
J'ai verifier les paramètres, ma version de Java, etc, mais dès que j'éxecutais le script "StartSonar.bat" il m'affichais uniquement "Starting SonarQube..." avant de s'arrêter.
Je n'ai donc pas pu l'installer sur le Jenkins, mais j'ai tout de même recherché comment l'utiliser depuis le pipeline, avec la commande suivante, qui n'est cependant pas incluse dans le Jenkinsfile afin qu'il puisse fonctionner. 

stage('SonarQube analysis') {
    withSonarQubeEnv(credentialsId: 'MyCredentials', installationName: 'My SonarQube Server') 
      bat 'mvn org.sonarsource.scanner.maven:sonar-maven-plugin:3.7.0.1746:sonar'
    }
	

TP réalisé par Pierre RASE