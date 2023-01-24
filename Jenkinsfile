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
          stage("Quality Gate") {
                      steps {
                          timeout(time: 1, unit: 'HOURS') {
                              // Parameter indicates whether to set pipeline to UNSTABLE if Quality Gate fails
                              // true = set pipeline to UNSTABLE, false = don't
                              waitForQualityGate abortPipeline: true
                          }
                      }
                  }

}
post {
      always {
        junit skipPublishingChecks: true, testResults: 'reports/junitT.html'
      }
   }

}