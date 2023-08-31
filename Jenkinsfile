pipeline {
    agent  any 
    tools { 
        maven 'mvn' 
    
    }
    
    stages {
        // Step 1
        stage('SCM') {
                steps {
                    git 'https://github.com/webdevprashant/jenkins-training-CI-CD-Day6.git'
                }        
        }
        // Step 2
        stage('Build') {
                   steps  {
                    
                    sh 'mvn clean package'
                }
        }
        
        // Step 3
        stage('Build docker image') {
                steps {
                    sh "sudo docker build -t webdevprashant/javaapp-day6:${BUILD_NUMBER} ."
                }
        }
        
        Redhat 8 CLI 2
        stage('Deploy webAPP in Prod Env') {
            steps {
               
            //   sshagent(['QA_ENV_SSH_CRED']) {                    
                        // sh "ssh root@192.168.43.229 docker rm -f myjavaapp"
                        // sh "ssh root@192.168.43.229 docker run  -d -p 8080:8080 --name myjavaapp webdevprashant/javaapp-day6:${BUILD_NUMBER}"                   
                // }
                sh "sudo docker rm -f myjavaappprodenv"
                sh "sudo docker run  -d -p 1224:8080 --name myjavaappprodenv webdevprashant/javaapp-day6:${BUILD_NUMBER}"  
            }
        }
    }
}      
