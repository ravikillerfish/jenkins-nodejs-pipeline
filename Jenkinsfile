pipeline {
   agent any
   stages {
      stage('checkout to git'){
	 steps {
	    git credentialsId: 'git-creds', url: 'https://github.com/ravikillerfish/jenkins-nodejs-pipeline.git'  
         }
      }
      stage('packiaging and sonarqube scaning'){
         steps {
            nodejs(nodeJSInstallationName: 'nodejs15.2.1') {
	       withSonarQubeEnv(credentialsId: 'sonarqube-secret') {
                     sh 'npm install'
                     sh 'npm run sonar'
               }
     \\          timeout(20) {
      \\            def quality = waitForQualityGate()
       \\           if (quality.status != 'OK') {
        \\             error "Pipeline aborted due to quality gate failure: ${qg.status}"
         \\         }
          \\     }

            }
         }
      }
 }
}
