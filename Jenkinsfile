def gv 


pipeline {

	agent any 

	environment{
	 	TEST = 'value'
	 	TEST@ = 'value'
	}

	tools{
		maven 'Maven'
	}

	parameters{
		string(name :'VERSION',defaultValue:'',description:'descrption for your job ')
		choice(name:"VERSION",choices:['1.1.0','1.2.0'],description:"")
		booleanParam(name :'executesTests',defaultView:true,description:'')
	}

	stages {
		stage("init"){
			steps{
				script{
					gv = load "script.groovy"
				}
			}
		}
		stage("build"){
			steps{
				script{
					gv.functionName()
				}
				echo 'This is a buils step'
				echo "This is my variable ${TEST}"
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
				withCredentials([
					usernamePasword(credentials:'server-credentials',usernameVariable:USER,passwordVariable:PWD)
				]){
					sh " some script ${USER} ${PWD}"
				}
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
