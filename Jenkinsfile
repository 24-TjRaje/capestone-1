pipeline {
  agent any
  environment {
    IMAGE_NAME = 'tjraje2157/casestudy-develop'
    DOCKER_CRED = credentials('d6a172ae-18ec-4888-b7de-04fdeb9dc756')
  }
  
  stages {
    stage("Switch Branch") {
	  steps {
	   
		sh "git checkout develop"
        sh "echo ${DOCKER_CRED_USR}"
		}
	}

    stage("Build the docker image") {
	  steps {
	    sh "docker build -t ${IMAGE_NAME}:${BUILD_NUMBER}"

		}
	}
    stage("Pushing the docker image") {
	  steps {
        sh "${DOCKER_CRED_PSW} | docker login -u ${DOCKER_CRED_USER} --password-stdin "
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