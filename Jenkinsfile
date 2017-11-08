node('docker') 
{
    docker.image('dcdevjbz/msbuild15:latest').inside("-v e:/workspace:c:/workspace")
    {
        stage('build')
        {
            msbuild --version
        }
    }
}