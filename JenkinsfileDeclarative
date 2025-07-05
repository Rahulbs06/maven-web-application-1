pipeline {
    
    agent any
    
    tools {
  maven 'Maven 3.9.8'
         }
         
    stages {
        stage ('Checkout Code')
             {
             steps{
                     git credentialsId: 'a7314d5b-25ce-4c6c-89fc-0d0881d2596a', url: 'https://github.com/MithunTechnologiesDevOps/maven-web-application.git'
                 }
             }    
        stage('Compile the code')      
            {
             steps{
                   sh 'mvn clean compile'
                 }
            }
        stage('Test the code')
              {
                  steps{
                     sh 'mvn test' 
                  }
              }
        stage('Build the package')
           {
               steps{
                   sh 'mvn clean package'
               }
           }
         stage('Build and Deploy the image'){
             steps{
                 sh "docker build -t rahulbs6/zero-to-hero:{BUILD_NUMBER} ."
                 sh 'dockes image ls'
                 sh 'docker login -u Rahulbs6 -p Docker@123'
                 sh "docker pull {BUILD_NUMBER}"
                 echo 'Image is built and pulled to repository'
             }
         }
        

        
        
    }  //stages closing
}      //pipeline closing

