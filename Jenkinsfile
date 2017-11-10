pipeline 
{
    agent none
        
    stages 
    {
        stage('Say Hello') 
        {
            steps 
            {
                dir("e:\\temp")
                {
                    git changelog: false, poll: false, url: 'https://github.com/jbogard/SharpSSH.git', branch: 'master'
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
