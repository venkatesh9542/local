
pipeline {

agent any;

tools{
maven "Maven3.8.6"
}

stages {

     stage ('checkout Git code'){
     steps {git credentialsId: 'Git-hub', url: 'https://github.com/venkatesh9542/maven-web-application.git'
     }//stepGitclosing
     }//stagegitclosing

     stage ('build'){
     steps {sh "mvn clean package"
     }//stepbuildclosing
     }//stagemvnbuildclosing
   
          stage ('Exec Sonar Report'){
     steps {sh "mvn  sonar:sonar"
     }//stepsonarclosing
     }//stagesonarclosing
    

      stage ('uploadArtifactToNexus'){
     steps {sh "mvn  deploy"
     }//stepsNexusclosing
     }//stageNexusclosing

       stage ('deploytoTomcat'){
     steps {
     sshagent(['Tomcat_Pem']){
     sh "scp -o StrictHostkeyChecking=no target/maven-web-application.war ec2-user@3.110.31.126:/opt/tomcat9/webapps/"}//shclosing
     }//stepsTomcatclosing
     }//stageTomcatclosing


}
}
