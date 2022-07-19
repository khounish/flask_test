//ALL environmental vars which jenkins provide are at jenkinsurl/env-vars.html
//http://cicdjenkinsnj.americaniche.com/env-vars.html/
//abc

pipeline {

    agent any

    environment {
        NEW_VERSION = "1.1.0"
        def scannerHome = tool 'SonarQube'
    }

    stages {

        stage ('build') {

            when {
                
                expression {
                    env.BRANCH_NAME != ""
                }

            }
            
            steps {
                echo 'building app'
                echo "VERSION in environment = ${NEW_VERSION}"
                sh 'pip install -r requirements.txt'
            }

        }

        stage ('test') {
            
            when {
                
                expression {
                    env.BRANCH_NAME != "main"
                }

            }

            steps {
                echo 'Testing app......'
            }

        }

        stage('SonarQube Analysis') {
            steps {
                echo 'SonarQube Analysis.....'
                withSonarQubeEnv('SonarQube') {
                // sh """${scannerHome}/bin/sonar-scanner
                // -D sonar.login=admin \
                // -D sonar.password=deepu08092000 \
                // -D sonar.sourceEncoding=UTF-8 \
                // -D sonar.language=python \
                // -D sonar.host.url=http://localhost:9000/
                // """

                sh """docker run --rm -v \$(pwd):/root/src --link sonarqube newtmitch/sonar-scanner sonar-scanner -D sonar.login="squ_22e9660dfd1b95aa043a05ecb5aafc817fd0c73f" -D sonar.language=python -D sonar.host.url=http://sonarqube.americaniche.com"""
             

                }
            }
        }

        stage ('deploy') {
            
            steps {
                echo 'deploying app'
                // sh 'flask run'
            }

        }
    }
}

// node {

//     //groovy script

// }
