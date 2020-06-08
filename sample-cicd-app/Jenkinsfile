
pipeline {
    
    agent{
        label "cicd"
    }

    stages{
        stage("build & deploy"){
            steps{
                echo "========executing A========"
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
                always{
                    echo "========always========"
                }
                success{
                    echo "========A executed successfully========"
                }
                failure{
                    echo "========A execution failed========"
                }
            }
        }
    }
    post{
        always{
            echo "========always========"
        }
        success{
            echo "========pipeline executed successfully ========"
        }
        failure{
            echo "========pipeline execution failed========"
        }
    }
}       