pipeline {
  agent any
  
  stages {
    stage("Switch Branch") {
	  steps {
	   
		sh "git checkout develop"
        sh "ls"
		}
	}

    stage("Build the code") {
	  steps {
	    sh "mvn clean install"
        sh "cp ./target/*.jar ."
		}
	}
  }


  post {
	success {
	  sh "echo Success"
	}
	
 }	
}