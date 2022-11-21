pipelin {
  agent any

  parameters {
    booleanParam(
      name: "RUN_INTEGRATION_TESTS", 
      defaultValue: true
    )
  }

  stages {
    stage('Test'){
      parallel {
        stage('Unit tests'){
          steps{
            ./mvnw test -D testGroups=unit
          }
        }
        stage('Integration tests'){
          when {
            expression { 
              return params.RUN_INTEGRATION_TESTS
            }
          }
          steps {
            ./mvnw test -D testGroups=integration
          }
        }
      }
    } 
  }

}
