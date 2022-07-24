pipeline {
    agent any
    tools {
      maven 'Maven 3.6.3'
      jdk 'jdk8'  
    }    
        stages {
            stage('Build') {
                steps {
                    sh 'mvn -f hello-app/pom.xml -B -DskipTests clean package'
                }
                post {
                    success {
                        echo "Now Archiving the Artifacts....."
                        archiveArtifacts artifacts: '**/*.jar'
                    }
                }
            }
            stage('Test') {
                steps {
                    sh 'mvn -f hello-app/pom.xml test'
                }
                post {
                    always {
                        junit 'hello-app/target/surefire-reports/*.xml'
                    }
                }
            }
        }
}
