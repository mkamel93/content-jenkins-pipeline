pipeline{
	
	agent {
		label 'master'
	}

	stages{
	
		stage('build'){
		steps{
			sh 'echo Building java files'
		 	sh 'javac -d . src/*.java'
			sh 'echo "Main-Class: Rectangulator" > MANIFEST.MF'
			sh 'jar -cmvf MANIFEST.MF rectangle.jar *.class'
		}
		}

		stage('run'){
		steps{
			sh 'echo running Java Code'
			sh 'java -jar rectangle.jar 8 10'
			
			}
		}
	}

	post{

		success{
			archiveArtifacts artifacts: 'rectangle.jar', fingerprint: true
		}
	}
}
