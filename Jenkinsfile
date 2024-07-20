pipeline {
  agent any
  environment {
    IMAGE_NAME = 'tjraje2157/casestudy-master'
    DOCKER_CRED = credentials('7f6b2922-1e31-4033-9b6b-ee057eafb26b')
  }
  
  stages {
    stage("Switch Branch") {
	  steps {
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
        sh 'docker login -u $DOCKER_CRED_USR --password $DOCKER_CRED_PSW'
	    sh "docker push ${IMAGE_NAME}:${BUILD_NUMBER}"
		}
	}
    stage("Spinning docker container") {
	  steps {
        sh 'docker stop case_study_master || true && docker rm case_study_master || true'
        sh 'docker run --name case_study_master -p 82:80 ${IMAGE_NAME}:${BUILD_NUMBER}'
		}
	}
  }


  post {
	success {
	  sh "echo container case_study_master_running successfully on port 82"
	}
     always {
      deleteDir() /* cleanup the workspace */
    }
	
 }	
}