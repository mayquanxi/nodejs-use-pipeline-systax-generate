pipeline {
        agent {
          label 'master'
        }
        triggers {
              pollSCM('H  H(6-18)/2 * * 1-6')
        }
        stages {
              stage('build') {
                steps {
                  nodejs('node') {
                    echo 'Install dependencies'
                    sh 'npm install'
                    sh 'npm start & sleep 10'
                    echo "access webapps before continue"
                    echo "address: http://172.18.0.2:3000"
                    input message: "did you check webapps, if you did it click Process to continue or didn't click Abort"
                  }
                }
              }
        }
}

//use pipeline systax for generate nodejs systax
