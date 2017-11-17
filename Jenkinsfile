pipeline {
  agent any
  stages {
    stage('Construct Builder') {
      steps {
        script {
          def out = powershell(returnStdout: true, script: 'if(( docker images -q mymsbuild ) -eq $null ) {docker build -f .\\MSbuild14_net47\\Dockerfile -t mymsbuild . } else {"mybuild image found"} ')
          println out
        }
        
      }
    }
    stage('Build') {
      steps {
        script {
          powershell(returnStdout: false, script: 'docker run -d --rm --name=service -t mymsbuild ')
          println powershell(returnStdout: true, script: 'docker exec service cmd /k msbuild.exe')
          println powershell(returnStdout: true, script: 'docker stop service')
          def commonVar = 'var'
          println powershell(returnStdout: true, script: 'echo ${commonVar}')
        }
      }
    }
  }
}