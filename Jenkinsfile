pipeline{
agent any
 environment{
   PATH = "/home/ec2-user/apache-maven-3.6.3/bin:$PATH"

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
 
}
}



