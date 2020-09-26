pipeline{
agent any
stages{
stage('Scm'){
steps{
git "https://github.com/sri567/demomvn.git"
}
}
stage("Build")
{
steps{
sh ''' mvn package '''
}
}
}
}


