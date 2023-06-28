pipeline {
    agent {
        docker { image 'maven:3.8.1-openjdk-11' }

    }
     tools {
        jdk 'Java11'
        maven 'Maven3'
    }
    
    stages {
        stage("Cleanup Workspace") {
            steps {
                cleanWs()
            }
        }
        stage("Checkout from SCM") {
            steps {
                dir('/var/lib/jenkins/workspace/project2-maven') {
 
                    git branch: 'main', credentialsId: 'github', url: 'https://github.com/bdino2005/complete-prodcution-e2e-pipeline'
                }
            }
        }
        stage("Build Application") {
            steps {
                dir('/var/lib/jenkins/workspace/project2-maven') {
 
                    sh "mvn clean package"
                }
            }
        }
        stage("Test Application") {
            steps {
                dir('/var/lib/jenkins/workspace/project2-maven') {
 
                    sh "mvn test"
                }
            }
        }
    }
}
