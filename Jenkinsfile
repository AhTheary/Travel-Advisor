pipeline {
    agent any
    stages{
        stage("run frontend"){
            steps {
                echo 'executing npm....'
                nodejs('Node'){
                    sh 'npm install'
                }
            }
        }
    }
}
