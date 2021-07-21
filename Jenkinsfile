pipeline {
    agent any

    stages {
        stage('Testing Environment') {
            steps {
//        sh 'mvn test -Dtest=ControllerAndServiceSuite'
//		sh 'mvn test -Dtest=IntegrationSuite'
//        sh 'mvn test -Dmaven.test.failure.ignore=true'
		sh 'mvn package -DskipTests -fn'
                }
            }
        stage('Build') {
            steps {
		sh 'mvn package -DskipTests -fn'
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

