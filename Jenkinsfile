pipeline {
  agent any
  stages {
  stage('Test'){
              steps {
                  sh './gradlew test'
                  junit 'reports/junitT.xml'
              }
          }
}

}