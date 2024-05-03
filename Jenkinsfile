pipeline{
    agent any
    tools{
        maven 'maven'
    }
    stages{
        stage('build maven'){
            steps{
                checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/chiehminchung/Hello-Spring']])
                sh 'mvn clean install'
            }
        }
        stage('build docker image'){
                    steps{
                        script{
                            sh 'docker build -t chiehmin/hello-spring .'
                        }

                    }
        }




    }



}