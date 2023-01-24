pipeline {
  agent any
  stages {
  stage('Test'){
              steps {
                  bat './gradlew test'
              }
          }
}
post {
      always {
        junit '**/reports/junit/*.xml'
      }
   }

}