node{
      // def mvnHome = tool name: 'maven 3.5.4', type: 'maven' 
      stage('Checkout'){
         git 'https://github.com/anilchelluru/java-tomcat-maven-example'
       
      }  
      stage('Build'){
         //// Get maven home path and build
        //sh "${mvnHome}/bin/mvn clean package -Dmaven.test.skip=true"
          sh "mvn clean package -Dmaven.test.skip=true"
      }
     stage ('Test-JUnit'){
         //sh "'${mvnHome}/bin/mvn' test surefire-report:report"
         sh "mvn test surefire-report:report"
      }  
    
      stage('Deploy') {     
            sshagent(['AWStomcat_login']) {
               // sh 'scp -o StrictHostKeyChecking=no target/tomcatdeploymnetdemo.war jenkins@35.193.54.220:/opt/tomcat/webapps'
               //sh 'scp -o StrictHostKeyChecking=no target/tomcatdeploymnetdemo.war root@18.116.241.40:/usr/local/tomcat/webapps'
               sh 'scp -o StrictHostKeyChecking=no target/tomcatdeploymnetdemo.war root@18.116.241.40:/opt/'
              
             }
         
      }
      
 }
