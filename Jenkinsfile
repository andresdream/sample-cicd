pipeline {
    
    agent {
        node {
            label 'cicd'
        }
    }

    options {
        buildDiscarder logRotator( 
                    daysToKeepStr: '16', 
                    numToKeepStr: '10'
            )
    }

    tools {nodejs "nodejs"}

    stages {

        /*stage('Cleanup Workspace') {
            steps {
                cleanWs()
                sh """
                echo "Cleaned Up Workspace For Project"
                """
            }
        }*/

        stage(' Unit Testing') {
            steps {                
                echo "Running Unit Tests"
                sh "pwd"
                sh "ls -la"
                /*sh "cd sample-app;npm test"*/
            }
        }

        stage('Code Analysis') {
            steps {
                sh """
                echo "Running Code Analysis"
                """
            }
        }

        stage('Build Deploy Code') {
            when {
                branch 'develop'
            }
            steps {
                echo "Packaging and deploying Serverless artifacts..."
                echo "BranchName: $BRANCH_NAME"
                /*samDeploy([
                    credentialsId: 'aws-fchaves-devops',
                    kmsKeyId: '',
                    outputTemplateFile: '',
                    region: 'us-east-1',
                    roleArn: '',
                    s3Bucket: 'sample-cicd-s3bucket',
                    s3Prefix: '',
                    stackName: 'dev',
                    templateFile: 'template.yaml']) */
            }
        }


    }

}
