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
                sh "${scannerHome}/bin/sonar-scanner"
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
