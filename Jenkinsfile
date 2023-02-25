pipeline {
      agent any
      stages {
            stage('Build') {
                     steps {
                           sh 'echo "Building ..."'
                           sh 'cd src/'
                           sh 'g++ helloworld.cpp -o helloworld'
                        }
               }

               stage('Test') {
                     steps {
                           sh 'echo "Running ..."'
                           sh 'cd src/'
                           sh './helloworld'
                        }
                  }
         }
   }
