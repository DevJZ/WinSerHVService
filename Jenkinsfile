pipeline 
{
    agent none
        
    stages 
    {
        stage('Say Hello') 
        {
            steps 
            {
                step
                {

                    checkout scm
                    
                }
                script
                {
                    node
                    {
                        def out = powershell(returnStdout: true, script: 'docker images')
                        println out
                    }
                    node
                    {
                        powershell(returnStdout: true, script: 'docker run -d -t msbuild15testplatform')
                    }                    
                }
            }
        }
    }
}
