pipeline {
	agent any
	stages {
		stage('Clone Repository') {
			steps {
				sh ''' #! /bin/bash
				ssh -i /var/lib/jenkins/.ssh/id_rsa root@13.233.238.59 '
				sudo rm -rf Pipeline-Chatapp/
				'
				scp -r /var/lib/jenkins/workspace/Pipeline-Chatapp root@13.233.238.59:
				'''
			}
		}
		stage('Build Image') {
			steps {
				sh ''' #! /bin/bash
				ssh -i /var/lib/jenkins/.ssh/id_rsa root@13.233.238.59 '
				cd Pipeline-Chatapp/
				docker stop $(docker ps -a -q)
				docker rm $(docker ps -a -q)
				docker rmi -f Pipeline-Chatapp_chatapp:latest bhushan25/chatapp
				docker-compose up -d
				'
				'''
			}
		}
		
	}
	post {
		always {
			echo 'Stage is success'
		}
	}
}
