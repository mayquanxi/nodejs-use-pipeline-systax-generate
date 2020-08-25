pipeline {
        agent {
          label 'master'
        }
        //triggers {
         //     pollSCM('H  H(6-18)/2 * * 1-6')
        //}
        stages {
              stage('build') {
                steps {
                  rtNpmResolver (
                      id: 'resolver-nodejs',
                      serverId: 'jfrogserver',
                      repo: 'npm-local-dependencies'
                  )
                  rtNpmDeployer (
                      id: 'deployer-nodejs',
                      serverId: 'jfrogserver',
                      repo: 'npm-local'
                      // Attach custom properties to the published artifacts:
                      //properties: ['key1=value1', 'key2=value2']
                  )
                  rtNpmInstall (
                      // Optional tool name from Jenkins configuration
                      tool: 'nodejs',
                      // Optional path to the project root. If not set, the root of the workspace is assumed as the root project path.
                      path: '.',
                      // Optional npm flags or arguments.
                      //args: '--verbose',
                      resolverId: 'resolver-nodejs'
                  )
                  rtNpmPublish (
                      // Optional tool name from Jenkins configuration
                      //tool: 'npm-tool-name',
                      // Optional path to the project root. If not set, the root of the workspace is assumed as the root project path.
                      path: '.',
                      deployerId: 'deployer-nodejs'
                  )
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
