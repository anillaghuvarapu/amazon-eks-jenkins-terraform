pipeline {
    agent any
       triggers {
        pollSCM "* * * * *"
       }
    stages {
        stage('Build Application') { 
            steps {
                echo '=== Building Petclinic Application ==='
                sh 'mvn -B -DskipTests clean package' 
            }
        }
        stage('Test Application') {
            steps {
                echo '=== Testing Petclinic Application ==='
                sh 'mvn test'
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }
        stage('Build Docker Image') {
            when {
                branch 'master'
            }
            steps {
                echo '=== Building Petclinic Docker Image ==='
                script {
                    sh 'docker build -t anilklaghuvarapu/petclinic-spinnaker-jenkins .'
                }
            }
        }
        stage('Push Docker Image') {
            when {
                branch 'master'
            }
            steps {
                echo '=== Pushing Petclinic Docker Image ==='
                script {
          withCredentials([usernamePassword(credentialsId: 'dockerHubCredentials', passwordVariable: 'dockerHubPassword', usernameVariable: 'dockerHubUser')]) {
          sh "docker login -u ${env.dockerHubUser} -p ${env.dockerHubPassword}"
          sh 'docker push anilklaghuvarapu/petclinic-spinnaker-jenkins:latest'
                    }
                }
            }
        }
        stage('Remove local images') {
            steps {
                echo '=== Delete the local docker images ==='
                sh("docker rmi -f anilklaghuvarapu/petclinic-spinnaker-jenkins:latest || :")
                #sh("docker rmi -f anilklaghuvarapu/petclinic-spinnaker-jenkins:$SHORT_COMMIT || :")
            }
        }
    }
}
