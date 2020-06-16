pipeline {
  agent any
  environment
  	{
  		VERSION = '1.3.0'
  	}
  	
  stages {
    stage('Build') {
      steps {
        echo "Building the version {$VERSION}"
 		sh 'jenkins/build.sh'
      }
    }

    stage('Test') {
    	when {
    		expression {
    		    // Solo se ejecuta en las ramas de development y master
    			BRANCH_NAME == 'dev' || BRANCH_NAME == 'master' 
    		   }
    		}
      steps {
        echo 'Testing the application'
        sh 'jenkins/test.sh'
      }
    }

    stage('Deploy') {
      steps {
         when {
    		expression {
    			// Solo se ejecuta en las ramas de master
    			BRANCH_NAME == 'master' 
    		   }
    		}
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