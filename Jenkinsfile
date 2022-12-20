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
        stage('Run Unit Test Cases') {
            steps {
                sh 'mvn -Dmaven.test.failure.ignore=true install'
                }
             }
        stage('Check the Code Qulity') {
            environment {
            scannerHome = tool 'sonarqube'
                 }
            steps {
               withSonarQubeEnv('sonarqube') {
               sh "${scannerHome}/bin/sonar-scanner"
                        }
                   }
                }
         stage('Artifact upload') {
             steps {
           nexusPublisher nexusInstanceId: '1234', nexusRepositoryId: 'helloworldservlet', packages: [[$class: 'MavenPackage', mavenAssetList: [[classifier: '', extension: '', filePath: 'target/helloworld.war']], mavenCoordinate: [artifactId: 'hello-world-servlet-example', groupId: 'com.geekcap.vmturbo', packaging: 'war', version: '$BUILD_NUMBER']]]                
                  }
               }


         }

 }
