pipeline {
    agent any

    environment {
        registry = "theay003/devops"
        registryCredential = 'dockerhub_id'
        dockerImage = ''
    }

    stages{
        stage("run frontend"){
            steps {
                echo 'executing npm....'
                nodejs('Node'){
                  echo 'installing npm....'

                    sh 'npm install'
      
                  echo 'run npm....'
                    sh 'npm run build'
                  echo 'run npm dev....'
                    sh 'npm run dev' 
                }
            }
        }
//         stage("run image"){
//             steps {
//                 script {
//                     dockerImage = docker.build registry + ":$BUILD_NUMBER"
//                 }
//                 }
//             }
        
//         stage('Deploy Image') {
//             steps{
//                 script {
//                     docker.withRegistry( '', registryCredential ) {
//                         dockerImage.push()
//                     }
//                 }
//             }
//         }
//         stage('Docker Run') {
//             steps{
//                 script {
//                     dockerImage.run("-p 3000:3000 --rm --name mywebContainer")
//                 }
//             }
//         }
    }
}
