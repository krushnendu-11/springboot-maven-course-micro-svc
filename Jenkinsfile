pipeline{
    agent any
    tools{
        maven 'maven'
    }
    stages{
        stage('checkout the code'){
            steps{
                git url:'https://github.com/krushnendu-11/springboot-maven-course-micro-svc.git', branch: 'master'
            }
        }
        stage('build the code'){
            steps{
                sh 'mvn clean package'
            }
        }
stage('Docker Build') {
       agent any
       steps {
        sh 'docker build -t ericsson/springboot-maven-course-micro-svc:latest .'
      }
    }
       stage('Docker Push') {
      agent any
      steps {
        withCredentials([usernamePassword(credentialsId: 'dockerhub', passwordVariable: 'dockerHubPassword', usernameVariable: 'dockerHubUser')]) {
          sh "docker login -u ${env.dockerHubUser} -p ${env.dockerHubPassword}"
          sh 'docker push ericsson/springboot-maven-course-micro-svc:latest'
        }
      }


}

}
}

