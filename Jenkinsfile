properties([pipelineTriggers([githubPush()])])

node('linux') {   
	stage('Unit Tests') {    
		git 'https://github.com/stra8436/java-project.git'
		sh 'ant'
		sh 'ant -f test.xml -v'
    		junit 'reports/result.xml'   
	}   
	stage('Build') {    
		sh 'ant -f build.xml -v'   
	}  
  	stage('Deploy') {		
		sh 'aws s3 cp /workspace/java-pipeline/dist/*.jar s3://jenkins-s3bucket-113alwaw3qgul/'	
	} 
	stage('Report') {    
		withCredentials([[$class: 'AmazonWebServicesCredentialsBinding', accessKeyVariable: 'AWS_ACCESS_KEY_ID', credentialsId: 'ded99645-f496-4b05-8ad3-9276e197db95', secretKeyVariable: 'AWS_SECRET_ACCESS_KEY']]) {
    		sh 'aws cloudformation describe-stack-resources --region us-east-1 --stack-name jenkins'   
	}
}
}
