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
            withSonarQubeEnv('SonarQube') {
                                bat "./gradlew sonarqube"
                            }

            }
          }

          stage("Quality Gate") {
                      steps {
                          timeout(time: 1, unit: 'HOURS') {
                              def qg = waitForQualityGate()
                                          if (qg.status != 'OK') {
                                              error "Pipeline aborted due to quality gate failure: ${qg.status}"
                                          }
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