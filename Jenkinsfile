pipeline {
   agent any
   stages {
      stage('checkout to git'){
	 steps {
	    git credentialsId: 'git-creds', url: 'https://github.com/ravikillerfish/jenkins-nodejs-pipeline.git'  
   }
  }
 }
}
