pipeline{

	agent any

	environment {
		DOCKERHUB_CREDENTIALS=credentials('Sushmaprj')
	}

	stages {
	    
	    stage('gitclone') {

			steps {
				git  'https://github.com/SUSHMA0910/node-redis-mongo.git'
			}
		}

		stage('Build') {

			steps {
				sh 'docker build -t 8967554398/node:latest .'
			}
		}

		stage('Login') {

			steps {
				sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			}
		}
		
		stage('Push') {

			steps {
				sh 'docker push 8967554398/node:latest'
			}
		}
	}

	post {
		always {
			sh 'docker logout'
		}
	}

}
