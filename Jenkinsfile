pipeline {
    agent {
        docker {
            image 'maven:3-alpine'
            args '-v /root/.m2:/root/.m2'
        }
    }
    stages {
        stage('Build') {
            steps {
                sh 'mvn -B -DskipTests clean package'
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }
        stage('Deliver') { 
            steps {
                sh './jenkins/scripts/deliver.sh' 
            }
        }
        stage ('Send notification of the end of the job') {
           steps {
               echo "Job name $JOB_NAME"
sh ""echo "$NAME has $ADJECTIVE $PLURAL_NOUN"""
sh ""curl -X POST -H 'Content-type: application/json' --data '{"text":"Hello, World!"}' https://hooks.slack.com/services/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""
sh ""curl -X POST -H 'Content-type: application/json' --data '{"text":"Hello, World!"}' https://hooks.slack.com/services/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""
      }
    }
  }
}
