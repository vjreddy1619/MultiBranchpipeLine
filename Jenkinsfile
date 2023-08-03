pipeline{
    agent any
    stages{
        stage('ContinuousDownload'){
            steps{
                git 'https://github.com/intelliqittrainings/maven.git'
            }
        }
        stage('ContinuousBuild'){
            steps{
                sh 'mvn package'
            }
        }
        stage('ContinuousDeployment'){
            steps{
                deploy adapters: [tomcat9(credentialsId: '2a78b56c-ab70-4db6-b92f-ca1eb4d7b8fb', path: '', url: 'http://172.31.86.188:8080')], contextPath: 'mytestapp', war: '**/*.war'
            }
        }
        stage('ContinuousTesting'){
            steps{
                git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
                sh 'java -jar /var/lib/jenkins/workspace/DeclarativePipeline1/testing.jar'
            }
        }
        stage('ContinuousDelivery'){
            steps{
                input message: 'waiting for approval of DM', submitter: 'kanna'
                deploy adapters: [tomcat9(credentialsId: '2a78b56c-ab70-4db6-b92f-ca1eb4d7b8fb', path: '', url: 'http://172.31.88.251:8080')], contextPath: 'myprodapp', war: '**/*.war'
            }
        }
    }
}
