pipeline {

    agent any

    stages {

        stage ('Build') {
            steps {
                withMaven() {
                    bat 'mvn clean package'
                }
            }
        }

        stage ('Deploy') {
            steps {

                withCredentials([[$class          : 'UsernamePasswordMultiBinding',
                                  credentialsId   : 'PCF_LOGIN',
                                  usernameVariable: 'USERNAME',
                                  passwordVariable: 'PASSWORD']]) {

                     bat 'cf login -a https://api.run.pivotal.io -u machunursainathgoud@gmail.com -p Sai@2236'
                     bat 'cf push'
                }
            }

        }

    }

}
