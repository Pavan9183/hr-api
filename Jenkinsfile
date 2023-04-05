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
//         stage('Tomcat Deploy - Dev') {
//             steps {
//                sshagent(['kumar']) {
//                           sh "scp -o StrictHostKeyChecking=no target/hr-api.war ec2-user@172.31.19.147:/opt/tomcat9/webapps/"
//                     sh "ssh ec2-user@172.31.19.147	 /opt/tomcat9/bin/shutdown.sh"
//                     sh "ssh ec2-user@172.31.19.147 /opt/tomcat9/bin/startup.sh"
//                 }
//             }
//         }

    }
}
