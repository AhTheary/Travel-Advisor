pipeline {
    agent any
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
    }
}
