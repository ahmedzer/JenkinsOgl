pipeline {
  agent any
  stages {
  stage('Test'){
              steps {
                  bat './gradlew test'
                  junit skipPublishingChecks: true, testResults: 'reports/junitT.html'
              }
          }
}

}