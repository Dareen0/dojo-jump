pipeline{

	agent any

	environment {
		DOCKERHUB_CREDENTIALS=credentials('dareen0-dockerhub')
	}

	stages {

		stage('Build') {

			steps {
				sh 'docker build -t dareen0/dojo-jump:latest .'
			}
		}

		stage('Login') {

			steps {
				sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			}
		}

		stage('Push') {

			steps {
				sh 'docker push dareen0/dojo-jump:latest'
			}
		}
	}

	post {
		always {
			sh 'docker logout'
		}
	}

}