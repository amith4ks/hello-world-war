pipeline {
    agent any	
	 
 stages {
      stage('checkout') {
           steps {             
                git branch: 'master', url: 'https://github.com/amith4ks/hello-world-war.git'             
          }
        }       

  stage('Docker Build and Tag') {
           steps {  
		 
                sh 'sudo docker build -t docker:1.0 .' 
                sh 'sudo docker tag samplewebapp amith4ks/docker:1.0' 
            }
        }

stage('Login to Docker hub') {
           steps {
              
                sh 'sudo docker login --username=amith4ks --password=Amith4@KS'
          }
        }
     
  stage('Publish image to Docker Hub') {
          
            steps {
       	  sh  'sudo docker push amith4ks/docker:1.0'  
        }                 
          
        }     
      stage('Run Docker container on Jenkins Agent') {
             
            steps 
	      {
                sh "sudo docker run -d -p 8006:8080 amith4ks/docker:1.0"
             }
        }
 
    }
	}
