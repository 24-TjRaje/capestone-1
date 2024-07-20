pipeline {
  agent any
  
  stages {
    stage("Switch Branch") {
	  steps {
	   
		sh "git checkout develop"
        sh "ls"
		}
	}
	  steps {
	    sh "mvn clean install"
		}
	}
}

  post {
	success {
	  sh "echo Success"
	}
	
}	
}