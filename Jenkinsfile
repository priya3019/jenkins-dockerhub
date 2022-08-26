pipeline{

	agent {label 'linux'}

	environment {
		DOCKERHUB_CREDENTIALS=credentials('1605724c-b81e-476f-9dbb-f1f9866f059b')
	}

	stages {
	    
	    stage('gitclone') {

			steps {
				git 'https://github.com/priya3019/jenkins-dockerhub.git'
			}
		}

		stage('Build') {

			steps {
				sh 'docker build -t priyappatil/nodeapp_test:latest .'
			}
		}

		stage('Login') {

			steps {
				sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			}
		}

		stage('Push') {

			steps {
				sh 'docker push priyappatil/nodeapp_test:latest'
			}
		}
	}

	post {
		always {
			sh 'docker logout'
		}
	}

}
