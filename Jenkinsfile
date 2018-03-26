node {
   def mvnHome
   stage('Code Checkout') { // for display purposes
      // Get some code from a GitHub repository
      git 'https://github.com/acmthinks/cloudconfigserver_acc.git'
      // Get the Maven tool.
      // ** NOTE: This 'M3' Maven tool must be configured
      // **       in the global configuration.           
      mvnHome = tool 'M3'
   }
   stage('Build') {
      // Run the maven build (let's clean up prior builds and get through to the package goal)
      if (isUnix()) {
         sh "'${mvnHome}/bin/mvn' -Dmaven.test.failure.ignore clean package"
      } else {
         bat(/"${mvnHome}\bin\mvn" -Dmaven.test.failure.ignore clean package/)
      }
   }
   stage('Unit Test') {
	  //run Junit test cases
      junit '**/target/surefire-reports/TEST-*.xml'
      //package the deployable code into a jar
      archive 'target/*.jar'
   }
   stage('Deploy (dev)') {
      //deploy to IBM Cloud (public)
      withCredentials([string(credentialsId: 'BLUEMIX', variable: 'bluemix_api')]) {
      	cf login --apikey $bluemix_api
      	cf target -o acm@us.ibm.com -s dev
      	cf logout
      }
   }
}