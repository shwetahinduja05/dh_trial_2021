node {
	def app
		
		stage('Clone repository') {
		  /* Make sure we have the repository cloned to our workspace */
		       checkout scm
		 }
		
		 stage('Build image') {
		       app = docker.build('shwetagithub05/mydockerrepo01')
		 }
		
		 stage('Test stage') {
		       app.inside{
		       sh 'echo "Test passed"'
		    }
		 }
		   
		  stage('Push image') {
		   /* We will push the image to docker hub with two tags:
		    * first, the incremental build number from Jenkins
		    * second, the 'latest' tag */
		         docker.withRegistry('https://hub.docker.com/', 'docker-hub-credentials'){
			 app.push("$(env.BUILD_NUMBER)")
			 app.push("latest")
		     }
		 }
	}
