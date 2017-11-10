pipeline 
{
    agent none
        
    stages 
    {
        stage('Build')
        {
            agent any
            steps
            {   
                ws("e:\tmp")
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
                            powershell(returnStdout: true, script: 'docker run -d -v "e:/tmp:c:/source" -t msbuild15testplatform')
                        }                    
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
