pipeline {
    agent any
      triggers {
        cron('*/2 * * * *')
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
                   sshPublisher(publishers: [sshPublisherDesc(configName: 'Docker-host', transfers: [sshTransfer(cleanRemote: false, excludes: '', execCommand: 'docker rmi -f april14:v.${BUILD_NUMBER}; docker build -t april14:v.${BUILD_NUMBER} .; docker tag april14:v.${BUILD_NUMBER} joelarnaud/april14:v.${BUILD_NUMBER}; docker push joelarnaud/april14:v.${BUILD_NUMBER}; docker run -dit -p 8080:8080 joelarnaud/april14:v.${BUILD_NUMBER}', execTimeout: 120000, flatten: false, makeEmptyDirs: false, noDefaultExcludes: false, patternSeparator: '[, ]+', remoteDirectory: '', remoteDirectorySDF: false, removePrefix: 'webapp/target', sourceFiles: '**/*.war')], usePromotionTimestamp: false, useWorkspaceInPromotion: false, verbose: false)])
                  
     }
    }
  }
}
