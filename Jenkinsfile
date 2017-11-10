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
                    def out = powershell(returnStdout: false, script: 'Write-Output "PowerShell is mighty!"')
                }
            }
        }
    }
}
