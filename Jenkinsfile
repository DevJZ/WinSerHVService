pipeline 
{
    agent none
        
    stages 
    {
        stage('one')
        {
            steps
            {
                node("checkout")
                {                    
                    checkout scm: [source: 'https://github.com/jbogard/SharpSSH.git']
                    powershell(returnStdout: true, script: 'docker run -d -v "./:c:/source"  -t msbuild15testplatform')
                }
            }

        }

        stage('two') 
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
                    node
                    {
                        powershell(returnStdout: true, script: 'docker run -d -t msbuild15testplatform')
                    }                    
                }
            }
        }
    }
}
