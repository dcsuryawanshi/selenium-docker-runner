pipeline{
	agent any
	stages{
		stage("Pull Latest Image"){
			steps{
				sh "docker pull dcsuryawanshi/iris_ras_nts"
			}
		}
		stage("Start Grid"){
			steps{
				sh "docker-compose up -d hub chrome"
			}
		}
		stage("Run Test"){
			steps{
				sh "docker-compose up iris-module"
			}
		}
	}
	post{
		always{
			archiveArtifacts artifacts: 'output/**'
			sh "docker-compose down"
			sh "sudo rm -rf output/"
		}
	}
}
