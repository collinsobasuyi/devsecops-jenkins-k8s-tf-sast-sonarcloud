pipeline {
    agent any
    tools { 
        maven 'Maven_3_5_2'  
    }
    stages {
        stage('Checkout repo and branch') {
            steps {
                git branch: 'dev',
                url: 'https://github.com/collinsobasuyi/devsecops-jenkins-k8s-tf-sast-sonarcloud.git'
            }
        }

        stage('install') {
            steps {	
		        sh 'mvn install'
			}
        } 

        stage('test') {
            steps {	
		        sh 'mvn test'
			}
        }

        stage('Compile and Run Sonar Analysis') {
            steps {	
		        sh 'mvn clean verify sonar:sonar -Dsonar.projectKey=collinsobasuyibuggywebapp -Dsonar.organization=collinsobasuyibuggywebapp -Dsonar.host.url=https://sonarcloud.io -Dsonar.token=bead2e4daf97e731cb011641d2986803a6c2f2c4'
			}
        } 
    }
}
