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
                    dir('e:\tmp')
                    {
                        checkout scm: [source: 'https://github.com/jbogard/SharpSSH.git'], poll: false
                    }
                    
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
