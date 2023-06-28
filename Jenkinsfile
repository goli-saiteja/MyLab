pipeline {
    //Directives
    agent any
    tools {
        maven 'maven'
    }
    environment {
        ArtifactId = readMavenPom().getArtifactId()
        Version = readMavenPom().getVersion()
        Name = readMavenPom().getName()
        GroupId = readMavenPom().getGroupId()
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
                nexusArtifactUploader artifacts: [[artifactId: '${ArtifactId}', classifier: '', file: 'target/VinayDevOpsLab-0.0.14-SNAPSHOT.war', type: 'war']], credentialsId: 'a6755651-3ee4-4457-b47e-ac936661615f', groupId: '${GroupId}', nexusUrl: '172.20.10.175:8081', nexusVersion: 'nexus3', protocol: 'http', repository: 'saidevopslab-SNAPSHOT', version: '${Version}'
            }
        }

        // Stage4: Print environment variables

        // Stage 4 : Print some information
        stage('Print Environment variables') {
            steps {
                echo "Artifact ID is '${ArtifactId}'"
                echo "Version is '${Version}'"
                echo "GroupID is '${GroupId}'"
                echo "Name is '${Name}'"
            }
        }

        // Stage5 : Publish the source code to Sonarqube
        stage('Deploy') {
            steps {
                echo ' Deploying'
            }
        }
    }
}
