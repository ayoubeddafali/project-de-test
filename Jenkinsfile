pipeline {
    agent {
      label 'master'
    }
    tools {
        maven 'maven-3.6.1'
    }
    stages {
        stage('Build') { 
            steps {
                sh "mvn clean compile"
            }
        }
        stage('Test') { 
            steps {
                sh "mvn clean test"
            }
        }
        stage('Sonar') { 
            steps {
                echo "Sonar"
                // sh  "mvn clean compile sonar:sonar -Dsonar.host.url=http://<URL_DE_SONAR> -Dsonar.login=<LOGIN> -Dsonar.password=<PASSWORD>"
            }
        }
        stage('Package') { 
            steps {
                sh  "mvn install"
            }
            post {
                success {
                    archiveArtifacts artifacts: "target/*.jar", fingerprint: true
                }
            }
        }

    }
}
