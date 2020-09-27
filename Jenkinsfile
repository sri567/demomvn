pipeline{
agent any
  environment{
    PATH  =  "/home/ec2-user/apache-maven-3.6.3/bin/mvn:$PATH"
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
}
}


