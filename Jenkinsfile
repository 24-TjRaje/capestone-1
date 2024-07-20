pipeline {
  agent any
  
  stages {
    stage("Clone Code") {
	  steps {
	    echo "Hello world"
		sh "git clone https://github.com/24-TjRaje/capestone-1.git"
		sh "cd capestone-1"
		sh "git checkout develop"
		}
	}
    stage("Build Code") {
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