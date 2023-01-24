pipeline {
  agent any
  stages {
  stage('Test'){
              steps {
                  bat './gradlew test'
                  bat './gradlew sonarqube'
              }

          }

}
post {
      always {
        junit skipPublishingChecks: true, testResults: 'reports/junitT.html'
      }
   }

}