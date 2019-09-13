pipeline {
    agent none
    stages {
	
	stage('Non-Parallel Stage') {
	    agent {
                        label "master"
                }
        steps {
                echo 'This stage will be executed first'
                }
        }

	
        stage('Run Tests') {
            parallel {
                stage('Test On Windows') {
                    agent {
                        label "Windows_Node"
                    }
                    steps {
                        echo "Task1 on Agent"
                    }
                    
                }
                stage('Test On Master') {
                    agent {
                        label "master"
                    }
                    steps {
						echo "Task1 on Master"
					}
                }
            }
        }
    }
}

/*
pipeline{
	agent any
	stages {
		stage('Compile'){
			steps {
			        echo "checking out project";
			        //git credentialsId: '9c9cf681-10cc-4838-aa28-e3d519ad661e', url: 'https://github.com/bhardwajkumar-pravesh/scripted-pipeline.git';
			        git 'https://github.com/bhardwajkumar-pravesh/scripted-pipeline.git'
			        echo 'project checked out correctly';
			        //bat label: '', script: 'Build.bat';
			        sh label: '', script: ' bash Build.sh';
					echo "Compiled Successfully !!" ;
			}
		}
		stage('JUnit'){
			steps{
			        //bat label: '', script: 'Unit.bat'
			        sh label: '', script: ' bash Unit.sh';
					echo "Junit Passed Successfully !!";
			}
		}
		stage ('Deploy'){
			steps {
			        //bat label: '', script: 'Deploy.bat'
			        sh label: '', script: ' bash Deploy.sh';
					echo "App Deployed Successfully !!";
			}
		}
		
		stage('Quality-Gate'){
			steps{
			        //bat label: '', script: 'Quality.bat'
			        sh label: '', script: ' bash Quality.sh';
					echo "SonarQube Quality Gate passed successfully !!";
			}
		}
	}
	post {
		always {
			echo "This is a block that will run always !!"
		}
		success {
			echo "This will run only if successful !!"
		}
		failure {
			echo 'This block will run only if failed'
		}
		unstable {
			echo 'This will run only if the run was marked as unstable means some test cases are passing and some tests are failig'
		}
		changed {
			echo ' This block will execute if Jenkins find change in staus from previous build to this build'
		}
	}
}
*/
