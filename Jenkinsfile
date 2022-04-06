node{

   def tomcatWeb = 'C://apache-tomcat-9.0.46//webapps'
   def tomcatBin = 'C://apache-tomcat-9.0.46//bin'
   def tomcatStatus = ''
   stage('SCM Checkout'){
     git 'https://github.com/nikhilpatiltest/JenkinsWar.git'
   }
   stage('Compile-Package-create-war-file'){
      def mvnHome =  tool name: 'maven-3', type: 'maven'   
      bat "${mvnHome}/bin/mvn package"
      }

   stage('Deploy to Tomcat'){
     bat "copy target\\JenkinsWar.war \"${tomcatWeb}\\JenkinsWar.war\""
   }
      stage ('Start Tomcat Server') {
         sleep(time:5,unit:"SECONDS") 
         bat "${tomcatBin}\\startup.bat"
         sleep(time:100,unit:"SECONDS")
   }
}
