pipeline {
	agent any
	
	tools {
		maven 'Maven'
	}
	
	stages {
		stage('Check-Out') {
			steps {
				git branch: 'main' , url: 'https://github.com/LikithReddy0409/Exam3.git'
				}
		}
		stage('Debug') {
    steps {
        sh '''
        whoami
        echo $PATH

        google-chrome --version
        chromedriver --version

        which google-chrome
        which chromedriver

        ls -l /usr/bin/google-chrome

        find /root/.cache/selenium -type f 2>/dev/null

        env | grep -i chrome
        '''
    }
}
		
		stage('Build') {
			steps {
				
					sh 'mvn clean package'
				
			}
		}
		
		stage('Test') {
				steps {
					
					sh 'mvn clean test'
				
			}
		}
		
		stage('Run-applciation') {
			steps {
				
				sh 'mvn exec:java -Dexec.mainClass="com.example.App"'
			
		    }		
		}
		
	}
	
	post {
		success {
			echo 'Build and Deploy Successful!'
		}
		failure {
			echo 'Build Failed!'
		}
	}
}
	
	
