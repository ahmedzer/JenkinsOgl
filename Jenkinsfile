pipeline {
  agent any
  stages {
  stage('Test'){
              steps {
                  bat './gradlew test'

              }

          }
          stage('sonar') {
            steps {

                                bat "./gradlew sonarqube"


            }
          }

          stage("Quality Gate") {
                      steps {
                          timeout(time: 1, unit: 'HOURS') {
                              waitForQualityGate abortPipeline: true
                          }
                      }
                  }

}
post {
      always {
        junit skipPublishingChecks: true, testResults: 'build/test-results/test/TEST-Matrix.xml'
      }
   }
}