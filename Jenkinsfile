pipeline {
    agent any
    stages{
        stage("run frontend"){
            steps {
                echo 'executing nuxt..'
                nodejs('Node'){
                    sh 'yarn install'
                }
            }
        }
    }
}
