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
        stage('push image dockerhub'){
            steps{
                script{
                withCredentials([usernameColonPassword(credentialsId: '2de180c4-5b92-4f7e-a2c5-c7c27d035e55', variable: 'hello variable')]) {
                    sh 'docker login -u $chiehmin -p $hello variable'
                }
                sh 'docker push chiehmin/hello-spring'


                }

            }
        }




    }



}