pipeline {
    agent {
        docker { image 'maven:3.8.1-adoptopenjdk-11' }
    }
    tools {
        jdk 'java11'
        maven 'Maven3'
    }
    environment {
        JAVA_HOME = "/usr/bin/java"
    }
    stages {
        stage("Cleanup Workspace") {
            steps {
                cleanWs()
            }
        }
        stage("Checkout from SCM") {
            steps {
                git branch: 'main', credentialsId: 'github', url: 'https://github.com/bdino2005/complete-prodcution-e2e-pipeline'
            }
        }
        stage("Build Application") {
            steps {
                withEnv(["JAVA_HOME=${env.JAVA_HOME}"]) {
                    sh "mvn clean package"
                }
            }
        }
        stage("Test Application") {
            steps {
                withEnv(["JAVA_HOME=${env.JAVA_HOME}"]) {
                    sh "mvn test"
                }
            }
        }
    }
}
