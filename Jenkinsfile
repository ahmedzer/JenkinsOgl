pipeline {
  agent any
  stages {
  stage('Test'){
              steps {
                  bat './gradlew test'
                  bat './gradlew sonarqube'
                  bat './gradlew detekt'
              }

          }

}
post {
      always {
        junit skipPublishingChecks: true, testResults: 'reports/junitT.html'
      }
   }

}