pipeline {
    agent any

    stages {
        stage('Compile') {
            steps {
                dir('C:\\Users\\ayanez3\\Desktop\\github\\ejemplo-maven'){
                   echo 'compile'
                   bat './mvnw.cmd clean compile -e'
                }
            }
        }
        stage('Unit') {
            steps {
                dir('C:\\Users\\ayanez3\\Desktop\\github\\ejemplo-maven'){
                    echo 'unit'
                    bat './mvnw.cmd clean test -e'
                }
            }
        }
        stage('Jar') {
            steps {
                dir('C:\\Users\\ayanez3\\Desktop\\github\\ejemplo-maven'){
                    echo 'jar'
                    bat './mvnw.cmd clean package -e'
                }
            }
        }
	stage('SonarQube') {
		steps {
			dir('C:\\Users\\ayanez3\\Desktop\\github\\ejemplo-maven'){
			    withSonarQubeEnv('sonar') { // You can override the credential to be used
			      bat 'mvn org.sonarsource.scanner.maven:sonar-maven-plugin:3.7.0.1746:sonar'
			    }
			}	
		}
	}	    
        stage('Run') {
            steps {
                dir('C:\\Users\\ayanez3\\Desktop\\github\\ejemplo-maven'){
                    echo '..echo de run'
                    bat 'start mvnw.cmd spring-boot:run'
                }
            }
        }
        stage('Test') {
           steps {
                echo '...echo de test'
			    sleep 20
				bat 'curl http://localhost:8081/rest/mscovid/estadoMundial'
		    }
        }        
    }
}
