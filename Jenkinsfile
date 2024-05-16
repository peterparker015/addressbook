pipeline {
    agent any

    stages {
        stage('SCM Checkout') {
            steps {
                echo 'Perfomr SCM Check-Out'
				echo 'Cloning Java Maven App Code'
				git 'https://github.com/peterparker015/addressbook.git'
            }
        }
        stage('Java Application Build') {
            steps {
                echo 'Perform Java Maven Application Build'
                sh 'mvn clean package'
            }
        }
        stage('Deploy to QA_Tomcat_Server') {
            steps {
 				script {
 				    sshPublisher(publishers: [sshPublisherDesc(configName: 'SA-Tomcat_Server', transfers: [sshTransfer(cleanRemote: false, excludes: '', execCommand: '', execTimeout: 120000, flatten: false, makeEmptyDirs: false, noDefaultExcludes: false, patternSeparator: '[, ]+', remoteDirectory: '.', remoteDirectorySDF: false, removePrefix: 'target/', sourceFiles: 'target/mvn-hello-world.war')], usePromotionTimestamp: false, useWorkspaceInPromotion: false, verbose: false)])
 				}
                
            }
        }
    }
}
