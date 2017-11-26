properties([pipelineTriggers([githubPush()])])

node('b02b4c3c1c8f') {   
	stage('Unit Tests') {    
		git 'https://github.com/stra8436/java-project.git'
		sh 'ant -f test.xml -v'
    		junit 'reports/result.xml'   
	}   
	stage('Build') {    
		sh 'ant -f build.xml -v'   
	}  
  	stage('Deploy') {    
		aws s3 cp /workspace/java-pipeline/dist/rectangle-3.jar s3://jenkins-s3bucket-113alwaw3qgul.s3.amazonaws.com/rectangle-3.jar   
	} 
	stage('Report') {    
		
	}
}
