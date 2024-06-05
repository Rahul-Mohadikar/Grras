pipeline{
	agent any
		parameters{
		choice( name: 'ENV', Choices: ['QA','UAT','DEV'], description: 'pick any enviornment')}
		triggers{
			pollSCM('* * * * *')}
		stages{
			stage(checlkout){
				steps{
					checkout scm}}
			stage('build'){
				steps{
					sh '/home/rahul/devops/apach-maven-3.9.6/bin/mvn install'}}
			stage('deployment'){
				steps{
					script{
						if ( env.ENV =='QA'){
					sh 'cp target/Grras.war /home/rahul/devops/apache-tomcat-9.0.88/webapps'
					echo 'Deployment has been done!'}
						else(env.ENV == 'UAT'){
					sh 'cd target/Grras.war /home/rahul/devops/apache-tomcat-3.9.6/webapps'
					echo 'Deployment has been done!'}
					echo 'Deployment failed!'}}}}
}
