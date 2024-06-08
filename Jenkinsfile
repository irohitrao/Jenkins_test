pipeline {
  agent any
  stages {
    stage('Executing math shell script') {
      steps {
        script {
          try {
            def ADD_RESULT = sh returnStdout:true, script: '''
#!/bin/bash
pwd '''

            def MULTIPLICATION_RESULT = sh returnStdout:true, script: '''
#!/bin/bash
"df -h ."
'''

            env.ADD_RESULT=ADD_RESULT
            env.MULTIPLICATION_RESULT=MULTIPLICATION_RESULT
          }
          catch(e) {
            println(e.toString())
            error 'Aborting the build as Executing math shell script stage failed.'
          }
        }

      }
    }

    stage('Printing math shell script output') {
      steps {
        script {
          try {
            println("printing ADDITION result")
            println(env.ADD_RESULT)

            println("printing MULTIPLICATION result")
            println(env.MULTIPLICATION_RESULT)

          }
          catch(e) {
            println(e.toString())
            error 'Aborting the build as Printing math shell script output stage failed.'
          }
        }

      }
    }

  }
}