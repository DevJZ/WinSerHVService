pipeline 
{
    agent none
    stages 
    {
        stage('Say Hello') 
        {
            steps 
            {
                script
                {
                    node
                    {
                        def out = powershell(returnStdout: true, script: 'docker images')
                        println out                        
                    }

                    node("docker run")
                    {
                        powershell(returnStdout: true, script: 'docker run -d -t msbuild15testplatform')
                    }
                }
            }
        }
    }
}
