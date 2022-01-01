pipeline {
      agent any
      stages {
            stage('Init') {
                  steps {
                        echo 'Hi, this is Faidon'
                        echo 'We are Starting the Testing'
                  }
            }
            stage('Build') {
                  steps {
                        echo 'Building Sample Maven Project'
                        sh 'mvn -f java-tomcat-sample/pom.xml clean package'
                  }
                  post {
                        success{
                              echo "Now archiving the Artifacts..."
                              archiveArtifacts artifacts: '**/*.war'
                        }
                  }
            }
            stage('Deploy in Staging Environment') {
                  steps {
                        echo "Deploying in Staging Area"
                  }
            }
            stage('Deploy Production') {
                  steps {
                        timeout(time:5,  unit:'DAYS'){
                              input message:'Approve PRODUCTION Deployment?'
                        }
                        echo "Deploying in Production Area"
                  }
            }
      }
}
