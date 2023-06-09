pipeline{
  agent any
  tools {
    maven 'Maven3'
  }
  stages{
    stage("Git Checkout"){
      steps{
         git branch: 'master', credentialsId: 'github-ID', url: 'https://github.com/demodevops2/java-hello-world-webapp.git'
}
}
   stage("Maven Build"){
     steps{
         sh "mvn clean package"
         sh "mv target/*.war target/myweb.war"
}
}

    stage("Deploy-war-file"){
      steps{
        sshagent(['Tomcat-EC2-ID']) {
          sh "scp -o StrictHostKeyChecking=no target/myweb.war ubuntu@172.31.5.222:/var/lib/tomcat9/webapps"
    
}
}
}

}
}
