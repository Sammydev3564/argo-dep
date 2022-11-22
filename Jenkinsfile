pipeline{

	agent any

	environment {
		DOCKERHUB_CREDENTIALS=credentials('dockerhublogin')
	}

	stages {

		stage('Build') {

			steps {
				sh 'docker build -t sammydev3564/argo:latest .'
			}
		}

		stage('Login') {

			steps {
				sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			}
		}

		stage('Push') {

			steps {
				sh 'docker push sammydev3564/argo:latest'
			}
		}
	}

	post {
		always {
			sh 'docker logout'
		}
	}

}
