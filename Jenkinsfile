pipeline {
    agent any 
    tools { 
        // Install the Maven version configured as "M3" and add it to the path.
        maven "maven"

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
