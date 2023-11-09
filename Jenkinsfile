pipeline {
	agent any
	parameters {
		choice(name: 'ENVIRONMENT', choices: ['QA','UAT'], description: 'Pick Environment value')
	}
	stages {
	    stage('Checkout') {
	        steps {
			checkout scm			       
		      }}
		stage('Build') {
	           steps {
		         sh '/home/swapnil/Documents/DevOps-Software/apache-maven-3.9.4/bin/mvn install'
	                 }}
		stage('Deployment'){
		   steps {
		sh 'cp target/CICD.war /home/swapnil/Documents/DevOps-Software/apache-tomcat-9.0.79/webapps'
			}}
		stage('slack notification'){
		    steps {
			slackSend baseUrl: 'https://hooks.slack.com/services/', channel: '#grras-test', color: 'good', message: 'welcome slack grras channel', teamDomain: 'devops', tokenCredentialId: 'testtoken'
			}}
}}
