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
                    powershell(returnStdout: false, script: 'Write-Output "PowerShell is mighty!"')
                }
            }
        }
    }
}
