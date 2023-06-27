pipeline{
    agent{
         docker { image 'maven:3.8.1-adoptopenjdk-11' }
    }
    tools {
        jdk 'JDK11'
        maven 'Maven3'
    }
    environment {
       JAVA_HOME = '/usr/bin/jdk' 
    }
    
    
    
    stages{
        stage("Cleanup Workspace"){
            steps {
                cleanWs()
            }

        }
    
        stage("Checkout from SCM"){
            steps {
                git branch: 'main', credentialsId: 'github', url: 'https://github.com/bdino2005/complete-prodcution-e2e-pipeline'
            }

        }
        stage("build Application"){
            steps {
               sh "mvn clean package"
            }

        }
        stage("test Application"){
            steps {
               sh "mvn test"
            }

        }

    }
    
      
}

