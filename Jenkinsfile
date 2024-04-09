pipeline {

	agent any 

	stages {
		stage("build"){
			steps{
				echo 'This is a buils step'
			}
		}

		stage("test"){

			when{
				expression {
					BRANCH_NAME == 'master'
				}
			}
			steps{
				echo 'This is a test step'
			}
		}

		stage("deploy"){
			steps{
				echo 'This is deployment stage'
			}
		}

	}

	post {
		always {
			echo 'This is a always block'
		}
		success{
			echo 'This is a success block'
		}
		failure{
			echo 'This is a failure block'
		}
	}
}
