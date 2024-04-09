pipeline {

	agent any 

	stages {
		stage("build"){
			steps{
				echo 'This is a buils step'
			}
		}

		stage("test"){
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
			'This is a always block'
		}
		success{
			'This is a success block'
		}
		failure{
			'This is a failure block'
		}
	}
}
