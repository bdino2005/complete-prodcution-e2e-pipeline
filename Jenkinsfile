pipeline {
    agent {
        label  "agent1"
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
