pipeline 
{
    agent any
        
    stages 
    {
        stage('Construct Builder')
        {
            steps
            {
                script
                {
                    def out = powershell(returnStdout: true, script: 'if(( docker images -q mymsbuild ) -eq $null ) {docker build -f MSbuild14_net47\Dockerfile -t mymsbuild . } else {"mybuild image found"} ')
                    println out
                }
            }            
        }

        stage('Build')
        {
            steps
            {

                script
                {
                    powershell(returnStdout: false, script: 'docker run -d --name=service -t mymsbuild ')
                    powershell(returnStdout: true, script: 'docker exec service cmd /k "msbuild.exe --version"')
                }
            }
        }
    }
}
