pipeline {
   agent any
   stages {
      stage('checkout to git'){
	 steps {
	    git credentialsId: 'git-creds', url: 'https://github.com/ravikillerfish/jenkins-nodejs-pipeline.git'  
         }
      }
      stage('packiaging and sonarqube scaning'){
         agent {
            docker {
               image 'node:16.15.1'
            }
         }
         steps {
            script {
               withSonarQubeEnv(credentialsId: 'sonarqube-secret') {
                  sh 'npm install'
                  sh 'npm run sonar'
               }
               timeout(20) {
                  def quality = waitForQualityGate()
                  if (quality.status != 'OK') {
                     error "Pipeline aborted due to quality gate failure: ${qg.status}"
                  }
               }
            }
         }
      }
 }
}
