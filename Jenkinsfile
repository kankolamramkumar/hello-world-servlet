pipeline {
    agent any 
    tools { 
        // Install the Maven version configured as "M3" and add it to the path.
        maven "maven"

    }
    options { buildDiscarder(logRotator(numToKeepStr: '1')) }
    
    parameters {
        string envi
        string path
        }
stages { 
        stage('Checkout') {
            steps {
                // Get some code from a GitHub repository
                checkout([$class: 'GitSCM', branches: [[name: 'master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/kankolamramkumar/hello-world-servlet.git']]])
                }
             }
         }

}
