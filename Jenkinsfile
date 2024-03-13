pipeline {
    agent any
    
    stages {
        
        stage("checkout") {
            steps {
                git branch: 'main', url: 'https://github.com/TrifonisAth/course3-jenkins-gs-spring-petclinic.git'
            }
        }
        
        stage("build") {
            steps {
                sh "./mvnw package"
            }
        }
        
        stage("capture"){
            steps {
                // **/target/*.jar
                archiveArtifacts '**/target/*.jar'
                junit stdioRetention: '', testResults: '**/target/surefire-reports/TEST*.xml'
                jacoco()
            }
        }
    }
    
    // post {
    //     always {
    //         // email block here.
    //     }
    // }
}