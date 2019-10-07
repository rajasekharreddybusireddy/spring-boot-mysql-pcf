pipeline {

    agent any

    stages {

        stage ('Build') {
            steps {
               // withMaven(maven: 'maven') {
                    bat "mvn clean package"
                //}
            }
        }

        stage ('Deploy') {
            steps {

                withCredentials([[$class          : 'UsernamePasswordMultiBinding',
                                  credentialsId   : '4dde18ff-de45-4342-abde-44c41b6ae073',
                                  usernameVariable: 'USERNAME',
                                  passwordVariable: 'PASSWORD']]) {

                    sh 'cf login -a http://api.run.pivotal.io -u $USERNAME -p $PASSWORD'
                    sh 'cf push'
                }
            }

        }

    }

}