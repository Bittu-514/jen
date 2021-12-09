pipeline {
  agent {label 'main'}
  parameters {
    choice(choices: ['ONE', 'TWO', 'THREE', 'FOUR', 'FIVE'], name: 'CHOCIE_Param')
    booleanParam(defaultValue: true, description: '', name: 'BOOLEAN')
    text(defaultValue: '''default value for Multi Line''', name: 'MULTI_LINE_STRING')
    booleanParam(defaultValue: true, description: 'Description of the Job', name: 'Update_Param')
stage('2nd Stage'){
      steps{
        println('Hello CHOCIE-Param!! ' + CHOCIE_Param)
        println("Hello MULTI-LINE-STRING!! ${MULTI_LINE_STRING}")
        println('Hello STRING-PARAMETER!! ' + STRING_PARAMETER)
      }
    }
    stage('3rd Stage'){
      steps {
        script {
          sh("echo 'My Env command $SERVICE_CREDS' >> Test.txt")
        }
      }
    }
  }
}
