pipeline{
    //Directives
    agent any
    tools {
        maven 'Maven'
    }
    environment{
        ArtifactId = readMavenPom().getArtifactId() 
        Version = readMavenPom().getVersion()
        Name = readMavenPom().getName()
        GroupId = readMavenPom().getGroupId()
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
        stage ('Publish to Nexus'){
            steps {
                nexusArtifactUploader artifacts: 
                [[artifactId: "${ArtifactId}", 
                classifier: '', 
                file: "target/VinayDevOpsLab-0.0.4-SNAPSHOT.war", 
                type: 'war']], 
                credentialsId: '7055983e-1c49-4dcc-ac11-1bae5bf11968', 
                groupId: "${GroupId}", 
                nexusUrl: '172.20.10.70:8081', 
                nexusVersion: 'nexus3', 
                protocol: 'http', 
                repository: "${Project1DevOpsLab-SNAPSHOT}", 
                version: "${version}"
                
            }
        }

        // Stage4 : Deploying 
        stage ('Deploy'){
            steps {
                echo 'deploying......'
            }
        }

        // Stage 5 : Print some information
        stage ('Print Environment variables'){
                    steps {
                        echo "Artifact ID is '${ArtifactId}'"
                        echo "Version is '${Version}'"
                        echo "GroupID is '${GroupId}'"
                        echo "Name is '${Name}'"
                    }
                }
        
    }

}