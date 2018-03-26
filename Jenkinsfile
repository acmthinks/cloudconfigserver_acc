pipeline {
     
    tools {
    		maven "apache-maven-3.1.0"
    		jdk "default"
	}
	
	//run on any agent
	agent any
	
	
    stages {
        stage('Build') { 
            steps {
                echo "Checkout"
                // create a directory called "tmp" and cd into that directory
        			dir("tmp") {
          			// use git to retrieve the plugin-pom
          			git changelog: false, poll: false, url: 'git://github.com/acmthinks/cloudconfigacc.git', branch: 'master'
          			sh 'echo "M2_HOME: ${M2_HOME}"'
          			sh 'echo "JAVA_HOME: ${JAVA_HOME}"'
          			sh 'mvn clean verify -Dmaven.test.failure.ignore=true'
				} 
            }
        }
        stage('Test') { 
            steps {
                // 
            }
        }
        stage('Deploy') { 
            steps {
                // 
            }
        }
    }
}