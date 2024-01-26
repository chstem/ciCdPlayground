pipeline {
    agent any
    tools {
        nodejs 'yarn'
    }

    stages {
        stage('install') {
            steps {
                sh 'yarn'
            }
        }

        stage('test') {
            steps {
                sh 'yarn test'
            }
	    post {
                always {
                    junit '**/reports/**/*.xml'
                }
            }
        }
        
	stage('test end_to_end') {
            steps {
                sh 'yarn build'
                sh 'yarn test:e2e'
            }
	    post {
                always {
                    junit '**/reports/**/*.xml'
                }
            }
        }

    }
}
