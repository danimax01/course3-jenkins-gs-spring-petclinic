pipeline {
    agent any
    
    stages {
        
        stage("checkout") {
            steps {
                git branch: 'main', url: 'https://github.com/danimax01/course3-jenkins-gs-spring-petclinic'
                sh 'ls'
            }
        }
        
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
