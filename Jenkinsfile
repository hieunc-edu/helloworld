pipeline {
    agent {
        ecs {
            inheritFrom 'build-example-spot'
        }
    }
    options {
    	withAWS(region:'ap-southeast-1',credentials:'aws')
    }
    stages {
        stage("git checkout") {
            steps {
                git url: 'https://github.com/hieunc-edu/helloworld'
            }
        }
        stage('S3') {
            steps {
                echo 'Deploying to RDG AWS s3 bucket.'
                s3Upload(bucket: 'infinitelambda-statics-origin', includePathPattern:'**/*')
            }
        }
    }
}

