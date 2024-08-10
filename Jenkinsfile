pipeline {
    agent { label 'Jenkins-Agent' }
    tools { 
        jdk 'Java17'
        maven 'Maven3'
    }
    stages {
        stage("Cleanup workspace") {
            steps {
                cleanWs()
            }
        }

        stage("Checkout from SCM") {
            steps {
                git branch: 'main', credentialsId: 'github', url: 'https://github.com/bhartiyadonors/bhartiyadonors.github.io'
            }
        }

        stage("Build Application") {
            steps {
                dir('/home/ubuntu') {  // Ensure we are in the correct directory
                    sh "mvn clean package"
                }
            }
        }

        stage("Test Application") {
            steps {
                dir('/home/ubuntu') {  // Ensure we are in the correct directory
                    sh "mvn test"
                }
            }
        }
    }
}
