pipeline {

    agent any

    stages {

        stage ('Build') {
            steps {
                withMaven(maven: 'maven_3_5_0') {
                    'mvn clean package'
                }
            }
        }

        stage ('Deploy') {
            steps {

                withCredentials([[$class          : 'UsernamePasswordMultiBinding',
                                  credentialsId   : 'PCF_LOGIN',
                                  usernameVariable: 'USERNAME',
                                  passwordVariable: 'PASSWORD']]) {

                     'C:\Program Files\Cloud Foundry\cf login -a http://api.run.pivotal.io -u $USERNAME -p $PASSWORD'
                     'C:\Program Files\Cloud Foundry\cf push'
                }
            }

        }

    }

}