pipeline {
    agent any

    tools {
        maven '396'
        jfrog 'jfrog-cli'
    }

    environment {
        CI = true
        ARTIFACTORY_ACCESS_TOKEN = credentials('jfrog-token')
    }

    stages {
        stage('Build') {
            steps {
                script {
                    sh 'mvn clean install'
                }
            }
        }
        
        stage('Upload to Artifactory') {
            steps {
               
                    jf 'rt u target/demo1-0.0.1-SNAPSHOT.jar my-repo/ --url=http://20.205.127.105:8082/artifactory/ --access-token ${ARTIFACTORY_ACCESS_TOKEN}'
                
            }
        }
    }
}
