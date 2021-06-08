pipeline{
    //Directives
    agent any
    tools {
        maven 'Maven'
    }

    stages {
        // Specify various stage with in stages

        // stage 1. Build
        stage ('Build'){
            steps {
                sh 'mvn clean install package'
            }
        }

        // Stage2 : Testing
        stage ('Test'){
            steps {
                echo ' testing......'

            }
        }
        
        // Stage3 : Publish the artifacts to Nexus
        stage ('Publish'){
            steps {
                nexusArtifactUploader artifacts: [[artifactId: 'VinayDevOpsLab', classifier: '', file: 'target/VinayDevOpsLab-0.0.4-SNAPSHOT.war', type: 'war']], credentialsId: '7055983e-1c49-4dcc-ac11-1bae5bf11968', groupId: 'com.vinaysdevopslab', nexusUrl: '172.20.10.70:8081', nexusVersion: 'nexus2', protocol: 'http', repository: 'Project1DevOpsLab-SNAPSHOT', version: '0.0.4-SNAPSHOT'
            }
        }

        // Stage4 : Deploying 
        stage ('Deploy'){
            steps {
                echo 'deploying......'
            }
        }
        
    }

}