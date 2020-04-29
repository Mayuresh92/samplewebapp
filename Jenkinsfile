pipeline {
    agent {
        label "master"
    }
    
    environment {
        // This can be nexus3 or nexus2
        NEXUS_VERSION = "nexus3"
        // This can be http or https
        NEXUS_PROTOCOL = "http"
        // Where your Nexus is running
        NEXUS_URL = "localhost:8081"
        // Repository where we will upload the artifact
        NEXUS_REPOSITORY = "dvs-evn-spring"
        // Jenkins credential id to authenticate to Nexus OSS
        NEXUS_CREDENTIAL_ID = "nexus_credentials"
    }
    stages {
        stage("clone code") {
            steps {
                script {
                    // Let's clone the source
                    git 'https://github.com/Mayuresh92/samplewebapp.git';
                }
            }
        }
        stage("mvn build") {
            steps {
                script {
                    // If you are using Windows then you should use "bat" step
                    // Since unit testing is out of the scope we skip them
                    bat 'mvn clean install'
                }
            }
        }
        
        stage("publish to tomcat") {
            steps {
                bat '''copy C:\\Users\\Mayuresh.Marathe\\.jenkins\\workspace\\jenkinswebapppipeline\\target\\*.war C:\\Users\\Mayuresh.Marathe\\Desktop\\apache-tomcat-8.5.54\\webapps'''
            }
        }
       
    }
}
