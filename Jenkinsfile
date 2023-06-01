pipeline {
    agent {
        docker {
            image 'maven:3.8.1-eclipse-temurin-11'
            args '-v /root/.m2:/root/.m2'
        }
    }
    // environment {
    // DOCKERHUB_CREDENTIALS = credentials('dockerhub')
    // }
    stages {
        stage('Build') {
            steps {
                sh 'mvn -B -DskipTests clean package'
            }
        }
        stage('Test') { 
            steps {
                sh 'mvn test' 
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml' 
                }
            }
        }
        // stage("Build Docker file"){

        //     // agent { node 'master' }
        //         steps {
        //             sh 'docker build -t phuongvd7/simple-java:latest .'
        //         }
        // }
        // stage('Login') {
        //     steps {
        //         sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
        //     }
        // }
        // stage('Push') {
        // steps {
        //     sh 'docker push phuongvd7/simple-java'
        //     }
        // }
        //  }
        // post {
        //     always {
        //     sh 'docker logout'
        //     }
        // }
}
}