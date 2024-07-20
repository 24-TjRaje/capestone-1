pipeline {
  agent any
  environment {
    IMAGE_NAME = 'tjraje2157/casestudy-develop'
    DOCKER_CRED = credentials('7f6b2922-1e31-4033-9b6b-ee057eafb26b')
  }
  
  stages {
    stage("Switch Branch") {
	  steps {
	    sh "whoami ${DOCKER_CRED_USR} : ${DOCKER_CRED_PSW}"
		sh "git checkout develop"
		}
	}

    stage("Build the docker image") {
	  steps {
	    sh "docker build -t ${IMAGE_NAME}:${BUILD_NUMBER} ."

		}
	}
    stage("Pushing the docker image") {
	  steps {
        sh "docker login -u ${DOCKER_CRED_USR} -p ${DOCKER_CRED_PSW}"
	    sh "docker push -t ${IMAGE_NAME}:${BUILD_NUMBER}"
		}
	}
  }


  post {
	success {
	  sh "echo Image built successfully with name ${IMAGE_NAME}:${BUILD_NUMBER}"
	}
	
 }	
}