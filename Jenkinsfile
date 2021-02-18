pipeline{
agent any
environment{
    PATH="/opt/apache-maven-3.6.3/bin:$PATH"
  }
stages{
stage("build")
{
steps{
sh ''' mvn package '''
}
}
stage("archive")
 {
steps{  
archiveArtifacts artifacts: 'target/demoart-*', followSymlinks: false
}
 }
stage("build & SonarQube analysis") {
    
            steps {
              withSonarQubeEnv('sonarqube') {
                sh 'mvn clean package sonarqube:sonarqube'
              }
            }
          }
          stage("Quality Gate") {
            steps {
			sleep(60)
			  script{
                qg = waitForQualityGate('sonarqualitygate')
              if (qg.status == 'OK') {
			  echo "quality gate passed"
			  }
			  else{
                  error "Pipeline aborted due to quality gate failure: ${qg.status}"
             
                
				}
              }
            }
          }    
}
}
