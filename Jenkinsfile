node {
    def app

    stage('Clone repository') {
        checkout scm
    }

    stage('Build image') {
        app = docker.build('andy1976/example-app')
    }
    
    stage('Test') {
	app.inside {
            sh 'npm test'
	}
    }

    stage('Push image') {
        docker.withRegistry('https://registry.hub.docker.com', 'docker-hub-creds') {
            app.push('latest')
        }
    }
}
