pipeline {
    agent any

    stages {
        stage('scm') {
            steps {
                git branch: 'main', url: 'https://github.com/ANTONYDAVID96/spring-petclinic.git'
            }
        }
        stage('build') {
            steps {
               bat 'mvn clean'
               bat 'mvn install'
    }
}
     stage('build to image') {
            steps {
                script{
                    sh 'docker build -t antonydavid96/spring-petclinic .'
                }
}
}
 stage('push to hub') {
            steps {
                script{
                    withCredentials([string(credentialsId: 'docker', variable: 'docker_antony')]) {
                    sh 'docker login -u antonydavid96 -p ${docker_antony}'
}
           sh 'docker push antonydavid96/spring-petclinic'
                     }
                }
            } 
                    
}
}
