@Library('jhc') _   
pipeline {
    agent any

    stages {
        
         stage('Git Checkout') {
        when{
            expression{
                params.branchname == "develop"
            }   
        }
             steps {
                 git branch: "${params.branchname}", credentialsId: 'github-pavan', url: 'https://github.com/Pavan9183/hr-api'
             }
        }
        stage('Maven Build') {
             when{
            expression{
            params.branchname == "develop"
            }  
        }
            steps {
                sh 'mvn clean package'
            }
        }
        stage('Tomcat Deploy  Dev') {
            steps {
               tomcatDeploy()
                }
            }
     }
}
