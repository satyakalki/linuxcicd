node{

   def tomcatWeb = 'path for tomcat/webapps'
   def tomcatBin = 'path for tomcat/bin'
   def tomcatStatus = ''
   stage('SCM Checkout'){
     git 'https://github.com/satyakalki/cicd.git'
   }
   stage('Compile-Package-create-war-file'){ 
     sh "mvn package"
      }
/*   stage ('Stop Tomcat Server') {
            sh ''' @Echo off
              kilall tomcat
			   if [ "$? -eq 0" ]; then 
				echo " stopped";
				else
					echo running
                  "${tomcatBin}\\shutdown.sh"
                  sleep 10
               fi
'''
   }*/
   stage('Deploy to Tomcat'){
     sh "cp target/JenkinsPipeline.war \"${tomcatWeb}/JenkinsPipeline.war/""
   }
      stage ('Start Tomcat Server') {
         sleep 5 
         sh "${tomcatBin}\\startup.sh"
         sleep 10
   }
}