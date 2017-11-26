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
		   
	} 
	stage('Report') {    
		
	}
}
