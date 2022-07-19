//ALL environmental vars which jenkins provide are at jenkinsurl/env-vars.html
//http://cicdjenkinsnj.americaniche.com/env-vars.html/

CODE_CHANGES = getGitChanges()

pipeline {

    agent any

    environment {
        NEW_VERSION = "1.1.0"
    }

    stages {

        stage ('build') {

            when {
                
                expression {
                    env.BRANCH_NAME != "" && CODE_CHANGES == true
                }

            }
            
            steps {
                echo 'building app'
                echo 'VERSION in environment = ${NEW_VERSION}'
                sh 'pip install -r requirements.txt'
            }

        }

        stage ('test') {
            
            when {
                
                expression {
                    env.BRANCH_NAME != ""
                }

            }

            steps {
                echo 'testing app'
            }

        }

        stage ('deploy') {
            
            steps {
                echo 'deploying app'
                sh 'flask run'
            }

        }
    }
}

// node {

//     //groovy script

// }
