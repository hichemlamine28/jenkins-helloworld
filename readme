# 🚀 Jenkins HelloWorld Java

![Java](https://img.shields.io/badge/Java-11-blue?logo=java)
![Jenkins](https://img.shields.io/badge/Jenkins-Automated-orange?logo=jenkins)
![Build](https://img.shields.io/badge/build-passing-brightgreen)
![License](https://img.shields.io/github/license/hichemlamine28/jenkins-helloworld)
![Last Commit](https://img.shields.io/github/last-commit/hichemlamine28/jenkins-helloworld)
![Issues](https://img.shields.io/github/issues/hichemlamine28/jenkins-helloworld)
![Pull Requests](https://img.shields.io/github/issues-pr/hichemlamine28/jenkins-helloworld)
![Stars](https://img.shields.io/github/stars/hichemlamine28/jenkins-helloworld)
![Forks](https://img.shields.io/github/forks/hichemlamine28/jenkins-helloworld)
![Platform](https://img.shields.io/badge/platform-linux%20%7C%20windows-lightgrey)

Ce projet est un exemple minimaliste d’une **application Java Hello World**, avec un pipeline CI/CD via **Jenkins**.

Il contient :
- Un fichier `Jenkinsfile`
- Un fichier source `Main.java`
- Un script de compilation `build.sh`
- Une intégration prête pour Jenkins

### 📁 Structure du projet

jenkins-helloworld/

├── Jenkinsfile

├── README.md

├── src

│ └── Main.java

└── build.sh


```groovy

### ⚙️ Jenkinsfile – Pipeline déclaratif

```groovy
pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/hichemlamine28/jenkins-helloworld.git'
            }
        }

        stage('Build') {
            steps {
                sh './build.sh'
            }
        }

        stage('Test') {
            steps {
                echo 'Aucun test pour ce projet de démonstration.'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Déploiement fictif réussi ✅'
            }
        }
    }
}
```


🧪 Script de compilation build.sh

```bash
#!/bin/bash
mkdir -p out
javac -d out src/Main.java
echo "✅ Compilation réussie"
```

Rends-le exécutable :

```bash
chmod +x build.sh
```

🚀 Exécuter le programme
```bash
java -cp out Main
```

📦 Prérequis
Java JDK 11 ou supérieur

Jenkins installé (ou un environnement CI équivalent)

Git configuré dans Jenkins (HTTPS ou SSH)

📸 Exemple de sortie
r
Hello from Java!

🧼 Nettoyage
```bash
rm -rf out
```
📜 Licence
Ce projet est sous licence MIT — voir LICENSE pour plus d'informations.

✅ TODO
 Ajouter des tests automatisés

 Intégrer Maven ou Gradle

 Ajouter des étapes de déploiement réel (Docker, serveur distant, etc.)
