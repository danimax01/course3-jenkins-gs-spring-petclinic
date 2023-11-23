pipeline {
    agent any
    
    stages {
        
        stage("build") {
            steps {
                sh './mvnw package'
            }
        }
        
        stage("capture") {
            steps {
                archiveArtifacts artifacts: '**/target/*.jar'
            }
        }
        
        stage("test") {
            steps {
                junit '**/target/surefire-reports/TEST*.xml'
            }
        }
    }
    
    post {
        failure {
            //email about job status
            echo "Job failed"
        }
    }
}
