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
}
}
