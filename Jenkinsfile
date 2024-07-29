pipeline {
    agent any

    stages {

	stage('Checkout') {
            steps {
                // Checkout code from GitHub repository
                git credentialsId: 'gitcredentials',url :'https://github.com/sraj9506/ansible-project.git', branch: 'develop'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    sh "sudo docker build -t suryrajsinh9506/my-ansi-image ."
		    sh "sudo docker login --username suryrajsinh9506 --password Suryrajsinh@9506"
		    sh "sudo docker push suryrajsinh9506/my-ansi-image:latest"
                }
            }
        }

	stage('Run Tests'){
	    steps {
		script {
		    echo 'Test Running ...'
		}
            }
	}
    }

    post {
        always {
            echo 'Pipeline finished.'
        }
        success {
            echo 'Pipeline succeeded.'
        }
        failure {
            echo 'Pipeline failed.'
        }
    }
}
