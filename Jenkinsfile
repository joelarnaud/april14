pipeline {
    agent any
      triggers {
        cron('H */1 * * *')
      }
          tools { 
            maven 'M2_HOME'
      }
              stages{
                stage('Build'){
                  steps {
                    echo "Build step"
                      sh 'mvn clean'
                      sh 'mvn install'
                      sh 'mvn package'
       }
       }
               stage('test'){
                 steps {
                     echo "test step"
                         sh 'mvn test'
     }
     }
               stage('deploy'){
                steps {
                  echo "test deploy"
                   sshPublisher(publishers: [sshPublisherDesc(configName: 'Docker-host', transfers: [sshTransfer(cleanRemote: false, excludes: '', execCommand: 'docker rmi -f april15:v.${BUILD_NUMBER}; docker build -t april15:v.${BUILD_NUMBER} .; docker tag april15:v.${BUILD_NUMBER} joelarnaud/april15:v.${BUILD_NUMBER}; docker push joelarnaud/april15:v.${BUILD_NUMBER}; docker run -dit -p 2000:8080 joelarnaud/april15:v.${BUILD_NUMBER}', execTimeout: 120000, flatten: false, makeEmptyDirs: false, noDefaultExcludes: false, patternSeparator: '[, ]+', remoteDirectory: '', remoteDirectorySDF: false, removePrefix: 'webapp/target', sourceFiles: '**/*.war')], usePromotionTimestamp: false, useWorkspaceInPromotion: false, verbose: false)])
                  
     }
    }
  }
}
