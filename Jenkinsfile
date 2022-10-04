pipline {
    agent any
    stages{
        stage("run frontend"){
            steps {
                echo 'executing nuxt..'
                nodejs('Node'){
                    sh 'npm install'
                }
            }
        }
    }
}