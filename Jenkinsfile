pipeline {
    agent any

    stages {
        stage('Testing Environment') {
            steps {
                    sh 'mvn test -Dtest=ControllerAndServiceSuite -Dmaven.test.failure.ignore=true'
		    sh 'mvn test -Dtest=IntegrationSuite -Dmaven.test.failure.ignore=true'
                }
            }
        stage('Build') {
            steps {
		sh 'mvn package -DskipTests'
		sh 'docker build -t="christophperrins/simple-server:latest" .'
                }
            }
        stage('Deploy') {
            steps {
		sh 'docker push christophperrins/simple-server:latest'
            }
        }
    }
}

