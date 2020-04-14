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
                   sh 'mvn deploy'
                  
     }
    }
  }
}
