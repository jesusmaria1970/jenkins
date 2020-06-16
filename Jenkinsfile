pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        echo 'Building the application'
        sh 'jenkins/build.sh'
      }
    }

    stage('Test') {
      steps {
        echo 'Testing the application'
        sh 'jenkins/test.sh'
      }
    }

    stage('Deploy') {
      steps {
        echo 'Deploying the application'
        sh 'jenkins/deploy.sh'
      }
    }
	}
   post{
	always{
		echo 'Se ha ejecutado el pipeline'
		}
	success{
	    echo 'Se ha ejecutado el pipeline correctamente'
	}	
	failure{
		echo 'Se ha ejecutado el pipeline con fallos'
		}
	}
 
}