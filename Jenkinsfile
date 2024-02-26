pipeline {
    agent any
    tools { 
        maven 'Maven_3_5_2'  
    }
    stages {
        stage('Checkout repo and branch') {
            steps {
                git(
                    branch: 'dev',
                    url: 'https://github.com/collinsobasuyi/devsecops-jenkins-k8s-tf-sast-sonarcloud.git'
                )
            }
        }

        stage('Build the Java application') {
            steps {
                sh 'mvn install'
            }
        }

        stage('Test java Application') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Run SAST scan using SonarCloud') {
            steps {	
                sh """
                mvn clean verify sonar:sonar \\
                    -Dsonar.projectKey=collinsobasuyibuggywebapp \\
                    -Dsonar.organization=collinsobasuyibuggywebapp \\
                    -Dsonar.host.url=https://sonarcloud.io \\
                    -Dsonar.token=bead2e4daf97e731cb011641d2986803a6c2f2c4
                """
            }
        } 
    }
}
