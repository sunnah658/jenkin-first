pipeline{
   agent any
    parameters{
        string(name: 'version', defaultValue: '1.0.1', description: 'version')
        choice(name: 'environment', choices: ['dev', 'stage', 'prod'], description: 'chose an step')
    }
    stages{
        stage('build'){
            steps{
                echo "building image. version - ${params.version}"
            }
        }
        stage('dev env'){
            when{
                expression {params.environment == 'dev'}
            }
            steps{
                echo "dev environment"
            }
        }
        stage('staging env'){
            when{
                expression {params.environment == 'stage'}
            }
            steps{
                echo "stage environment"
            }
        }
        stage('production env'){
            when{
                expression {params.environment == 'prod'}
            }
            steps{
                echo "production environment"
            }
        }
    }
    post{
        SUCCESS {
            emailext subject: 'Build SUCCESS: ${JOB_NAME}',
                body: 'job ${JOB_NAME} build #${BUILD_NUMBER} was success',
                to: 'rajiulhaque658@gmail.com'
        }
        FAILURE {
            emailext subject: 'Build FAILURE: ${JOB_NAME}',
                body: 'job ${JOB_NAME} build #${BUILD_NUMBER} was failed',
                to: 'rajiulhaque658@gmail.com'
        }
    }
}
