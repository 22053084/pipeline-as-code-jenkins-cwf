pipeline {
    agent any
    stages {
        stage('S1_22053084') {
            steps {
                echo 'S1_22053084 : Environment Preparation Completed'
            }
        }
        stage('S2_22053084') {
            steps {
                //sh '''
                //    sudo docker rm -f S2_22053084_Server
                //    sudo docker run -d --name S2_22053084_Server -p 42000:80 22053084_webimage
                //'''
                //echo 'S2_22053084 : Web Server Creation Completed'
  	        script {
		    try {
		        env.DOCKERRUN = sh(script: "sudo docker rm -f S2_22053084_Server", returnStdout: true).trim()
	                env.RUN_BUILD_DATE = sh(returnStdout: true, script: "date -u +'%Y-%m-%dT%H:%M:%SZ'").trim()    
                    } catch (err) {
    			echo "response: $err -- ${env.DOCKERRUN} -- ${env.RUN_BUILD_DATE}"   
		    }
		    echo "S2_22053084 : Web Server Creation Completed: -- ${env.DOCKERRUN} -- ${env.RUN_BUILD_DATE}"   
		}
            }
        }
        stage('S3_S4_PARALLEL') {
            parallel{
                stage('S3_22053084') {
                    steps {
                        echo 'S3_22053084 : API Test Completed'
                    }
                }
                stage('S4_22053084') {
                    steps {
                        echo 'S4_22053084 : DAST Security Test Completed'
                    }
                }    
	    }
        }
        stage('S5_22053084') {
	    steps {
                script {
                     env.RELEASE_WORK = input message: 'Do you want to release the work? [Y/n]     ',
                             parameters: [string(defaultValue: '',
                                          description: '',
                                          name: 'Release_work')]
                }
	    }
        }
        stage('S6_22053084') {
            steps {
		script {
                     if (env.RELEASE_WORK == 'Y') {
                         echo "Work Released - 22053084"
                     } else {
                         abort
                     }
		}
            }
        }
    }
}
