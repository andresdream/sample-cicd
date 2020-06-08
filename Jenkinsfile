pipeline {
    
    agent{
        label "cicd"
    }

    stages{
        stage("Test") {
            steps{
                echo "Executing unit testing..."
                sh "cd helllo-world"
                sh "npm test"
            }            
        }
        stage("Deploy"){
            steps{
                echo "Executing SAM Build and Deploy..."
                samDeploy([
                    credentialsId: 'fchaves keys', 
                    kmsKeyId: '', 
                    outputTemplateFile: '', 
                    region: 'us-east-1', 
                    roleArn: '', 
                    s3Bucket: 'sample-cicd-s3bucket', 
                    s3Prefix: '', 
                    stackName: 'sample-cicd-stack', 
                    templateFile: 'template.yaml'])        
            }
            post{                
                success{
                    echo "Stage Build and Deploy success!"
                }
                failure{
                    echo "There was an error on stage Build & Deploy"
                }
            }
        }
    }
    post{        
        success{
            echo "Pipeline success!"
        }
        failure{
            echo "Pipeline failed!"
        }
    }
}       