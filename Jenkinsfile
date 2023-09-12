pipeline {
    agent any

    stages {
        stage('scmcheckout') {
            steps {
                git 'https://github.com/teluguhackerforfree/maven.git'
            }
        }
		   stage('compile') {
            steps {
                echo 'mvn compile'
				sh 'mvn compile'
            }
        }
		   stage('package') {
            steps {
                echo 'Hello World'
				sh 'mvn package'
            }
        }
		   stage('artifact') {
            steps {
                echo 'deploy package'
				deploy adapters: [tomcat9(credentialsId: 'tomcat-credential', path: '', url: 'http://15.206.123.85:8081/')], contextPath: 'dev', war: '**/*.war'
            }
        }
    }
}
