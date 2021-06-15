pipeline{
	agent any
	stages{
		stage("Pull Latest Image"){
			steps{
				bat "docker pull dcsuryawanshi/iris_ras_nts"
			}
		}
		stage("Start Grid"){
			steps{
				bat "docker-compose up -d hub chrome"
			}
		}
		stage("Run Test"){
			steps{
				bat "docker-compose up iris-module"
			}
		}
	}
	post{
		always{
			archiveArtifacts artifacts: 'output/**'
			bat "docker-compose down"
			bat "sudo rm -rf output/"
		}
	}
}
