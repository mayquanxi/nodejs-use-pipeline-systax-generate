pipeline {
        agent {
          label 'master'
        }
        triggers {
              pollSCM('H  H(6-18)/2 * * 1-6')
        }
        stages {
              nodejs('node') {
                steps {
                  sh 'npm install'
                }
              }
        }
}