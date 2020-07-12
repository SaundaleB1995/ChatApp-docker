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
				#docker-compose down 
				docker stop $(docker ps -a -q)
				docker rm $(docker ps -a -q)
				docker rmi -f Pipeline-Chatapp_chatapp:latest bhushan25/chatapp
				#docker rmi -f Pipeline-Chatapp_database:latest bhushan25/chatappdb
				#docker rmi -f Pipeline-Chatapp_nginx:latest bhushan25/chatappnginx
				docker-compose up -d
				#docker stop chatapplication
				#docker rm chatapplication
				#docker build -t chat .
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
