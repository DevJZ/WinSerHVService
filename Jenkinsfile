pipeline 
{
    agent none
        
    stages 
    {
        stage('Build')
        {
            agent
            {
                node
                {
                    customworkspace 'e:\tempworkspace'
                }
            }
            steps
            {   

                checkout scm 
                script
                {
                    node
                    {
                        def out = powershell(returnStdout: true, script: 'docker images')
                        println out
                    }
                    node
                    {
                        def workspace = pwd()
                        powershell(returnStdout: true, script: 'docker run -d --name buildservice -v "e:/tempworkspace:c:/source" -t msbuild15testplatform')
                    }                    
                }
            }
        }        
    }
}
