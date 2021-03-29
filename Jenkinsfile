pipeline {
    agent {
        ecs {
            inheritFrom 'build-example-spot'
        }
    }
    stages {
        stage("git checkout") {
            steps {
                git url: 'https://github.com/hieunc-edu/helloworld'
            }
        }
        stage('S3') {
            when {
                branch 'master'
            }
            steps {
                echo 'Deploying to RDG AWS s3 bucket.'
                s3Upload(bucket: 'infinitelambda-statics-origin', includePathPattern:'**/*')
            }
        }
    }
}

