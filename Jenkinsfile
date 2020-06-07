def CLIENT_DIR= "client"
def S3_BUCKET_NAME= "capston-todo"
pipeline{
    agent any
    stages{
        stage("Copy Secrets"){
            steps{
                    withCredentials([file(credentialsId: 'todo-client-master', variable: 'tconfig')]) {
                        sh "cp \$tconfig $CLIENT_DIR/src/config.ts"
                    }
            }
        }   
        stage("Build"){
            steps{
                dir("${env.WORKSPACE}//${CLIENT_DIR}"){
                    nodejs('node'){
                        sh "npm install"
                        sh "npm run build"
                    }
                }
            }
        }
        stage("Lint Html"){
            steps{
                dir("${env.WORKSPACE}//${CLIENT_DIR}/build"){
                    sh 'tidy -q -e *.html'
                }
            }
        }
        stage("Deploy to S3"){
            steps{
                dir("${env.WORKSPACE}//${CLIENT_DIR}"){
                    withAWS(region: 'us-east-1', credentials:'jenkins'){
                        s3Upload(bucket: "${S3_BUCKET_NAME}", workingDir:'build', includePathPattern:"**/*")
                    }
                }
            }
        }
    }
}