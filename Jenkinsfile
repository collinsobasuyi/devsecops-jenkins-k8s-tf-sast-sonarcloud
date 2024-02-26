pipeline {
  agent any
  tools { 
        maven 'Maven_3_5_2'  
    }
   stages{
    stage('CompileandRunSonarAnalysis') {
            steps {	
		sh 'mvn clean verify sonar:sonar -Dsonar.projectKey=collinsobasuyibuggywebapp -Dsonar.organization=collinsobasuyibuggywebapp -Dsonar.host.url=https://sonarcloud.io -Dsonar.token=bead2e4daf97e731cb011641d2986803a6c2f2c4'
			}
        } 
  }
}
