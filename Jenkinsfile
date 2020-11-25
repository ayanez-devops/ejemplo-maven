pipeline {
    agent any

    stages {
        stage('Compile') {
            steps {
                dir('C:\\Users\\ayanez3\\Desktop\\github\\ejemplo-maven'){
                   echo 'compile'
                   sh './mvnw.cmd clean compile -e'
                }
            }
        }
        stage('Unit') {
            steps {
                dir('C:\\Users\\ayanez3\\Desktop\\github\\ejemplo-maven'){
                    echo 'unit'
                    sh './mvnw.cmd clean test -e'
                }
            }
        }
        stage('Jar') {
            steps {
                dir('C:\\Users\\ayanez3\\Desktop\\github\\ejemplo-maven'){
                    echo 'jar'
                    sh './mvnw.cmd clean package -e'
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
			    sleep 10
				bat 'curl http://localhost:8081/rest/mscovid/estadoMundial'
		    }
        }        
    }
}
