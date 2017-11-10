pipeline 
{
    agent none
    stages 
    {
        stage('Say Hello') 
        {
            steps 
            {
                def out = powershell(returnStdout: true, script: 'Write-Output "PowerShell is mighty!"')
                println out
            }
        }
    }
}
