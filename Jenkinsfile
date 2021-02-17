pipeline{
agent any
stages{
stage("sc"){
steps{
git "https://github.com/sri567/demomvn.git"
}
}
stage("build")
{
steps{
sh ''' mvn package '''
}
}
}
}
