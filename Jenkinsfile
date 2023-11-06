pipeline {
    agent any 
triggers {
  pollSCM '*/1 * * * *'
}
    parameters {
  choice choices: ['Test', 'Test2', 'Stage', 'Stage2', 'Hotfix', 'Production'], description: 'Select the Environment and Start with the Build for the said environment', name: 'Select Environments'
}
    stages{
        stage('Code Download'){
            steps{
                git 'https://github.com/theshubhamgour/JenHash.git'
            }
        }
        stage('Maven Build'){
            steps{
                sh 'mvn clean install'
            }
        }
        stage('Hosting'){
            steps{
                sh 'cp target/JenHash.war home/theshubhamgour/Documents/softwares/apache-tomcat-9.0.82/webapps'
            }
        }
    }
}