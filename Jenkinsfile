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
                    sh 'yarn install'
                    sh 'yarn start & sleep 10'
                    echo "access webapps before continue"
                    echo "address: http://localhost:3000"
                    input message: "did you check webapps, if you did it click Process to continue or didn't click Abort"
                  }
                }
              }
        }
}