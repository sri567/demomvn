pipeline{
agent any
 environment{
   PATH = "/opt/apache-maven-3.6.3/bin:$PATH"

 }
stages{
stage('Scm'){
steps{
git "https://github.com/sri567/demomvn.git"
}
}
stage("Build")
{
steps{
sh "mvn package"
}
}
 
 stage("archiveArtifacts")
{
steps{
 archiveArtifacts artifacts: 'target/demoart-*', followSymlinks: false
}
}
 
 stage("SonarQube") {
                 withSonarQubeEnv('sonar') {
                 sh 'mvn clean package sonar:sonar'
                 
          }
      }
      
      stage("Quality Gate"){
          sleep(30) {
              def qg = waitForQualityGate()
              if (qg.status = 'OK') {
                  echo "quality gate passed"
              }
			  else {
			  error "Pipeline aborted due to quality gate failure: ${qg.status}"
			  
			  }
          }
      }  
 
}
}



