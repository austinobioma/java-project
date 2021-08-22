pipeline {
    agent any

    stages {
        stage('Git checkout') {
            steps {
                git 'https://github.com/austinobioma/java-project.git'
            }
        }
      stage('Build') {
            steps {
               sh 'cd MyWebApp && mvn clean  package'
            }
        }
      stage('Test') {
            steps {
                echo 'Hello World'
            }
        }
      stage('Deploy to tomcat') {
            steps {
                sshPublisher(publishers: [sshPublisherDesc(configName: 'tomcat-server', transfers: [sshTransfer(cleanRemote: false, excludes: '', execCommand: 'ansible-playbook -i hosts myplaybook.yml --limit ubuntu@54.242.174.212', execTimeout: 120000, flatten: false, makeEmptyDirs: false, noDefaultExcludes: false, patternSeparator: '[, ]+', remoteDirectory: '.', remoteDirectorySDF: false, removePrefix: 'webapp/target', sourceFiles: 'webapp/target/MyWebApp.war')], usePromotionTimestamp: false, useWorkspaceInPromotion: false, verbose: false)])
            }
        }
    }
          
}
