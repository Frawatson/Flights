pipeline {
    agent any
    
    environment {	
		DOCKERHUB_CREDENTIALS=credentials('Dockerhublogin')
		KUBERNETES_CREDENTIALS=credentials('kubeconfig')
	}

    stages {
        stage('Checkout') {
            steps {
                // Clone the Git repository
                checkout([$class: 'GitSCM', 
                          branches: [[name: '*/master']], 
                          doGenerateSubmoduleConfigurations: false, 
                          extensions: [], 
                          submoduleCfg: [], 
                          userRemoteConfigs: [[url: 'https://github.com/Frawatson/Flights.git']]])
            }
        }

        stage('Build Docker Image') {
            steps {
                // Build the Docker image using the Dockerfile
                sh 'docker build -t flights .'
            }
        }

        stage('Push Docker Image') {
            steps {
                // Push the Docker image to a container registry (replace <CONTAINER_REGISTRY> with your registry details)
                sh 'docker tag flights frawatson/flights:latest'
                sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
                sh 'docker push frawatson/flights:latest'
            }
        }

         stage('Deploy to Kubernetes') {
            steps {
                // Deploy the Docker image to a Kubernetes cluster
                script {
                    withKubeConfig(credentialsId: 'kubeconfig'){
			    sh "kubectl apply -f deployment.yaml"
			    sh "kubectl apply -f service.yaml"
		    }
                }
            }
        }
    }
}
