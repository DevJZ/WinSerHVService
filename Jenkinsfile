pipeline 
{
    agent none
        
    stages 
    {
        stage('Build')
        {
            agent none
            steps
            {                
                script
                {
                    node
                    {
                        def out = powershell(returnStdout: true, script: 'docker images')
                        println out
                    }
                    node
                    {
                        ws("tmp")
                        powershell(returnStdout: true, script: 'docker run -d --name buildservice -v "/tmp:c:/source" -t msbuild15testplatform')
                        checkout scm 
                    }                    
                }
            }
        }        
    }
}
