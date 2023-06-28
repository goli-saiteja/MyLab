pipeline {
    //Directives
    agent any
    tools {
        maven 'maven'
    }

    stages {
        // Specify various stage with in stages

        // stage 1. Build
        stage('Build') {
            steps {
                sh 'mvn clean install package'
            }
        }

        // Stage2 : Testing
        stage('Test') {
            steps {
                echo ' testing......'
            }
        }
        //stage3: Publish the artifact to Nexus

        stage('Publish to Nexus') {
            steps {
                nexusArtifactUploader artifacts: [[artifactId: 'VinayDevOpsLab', classifier: '', file: 'target/VinayDevOpsLab-0.0.13-SNAPSHOT.war', type: 'war']], credentialsId: 'a6755651-3ee4-4457-b47e-ac936661615f', groupId: 'com.vinaysdevopslab', nexusUrl: '172.20.10.175:8081', nexusVersion: 'nexus3', protocol: 'http', repository: 'saidevopslab-SNAPSHOT', version: '0.0.13-SNAPSHOT'
            }
        }

        // Stage3 : Publish the source code to Sonarqube
        stage('Deploy') {
            steps {
                echo ' Deploying'
            }
        }

    }
}
