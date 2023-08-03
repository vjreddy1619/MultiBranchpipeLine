@Library('mylib')_
pipeline{
    agent any
    stages{
        stage('ContinouosDownload_Loans'){
            steps{
                script{
                    cicd.gitDownload("maven")
                }
            }
        }
        stage('ContinouosBuild_Loans'){
            steps{
                script{
                    cicd.mavenBuild()
                }
            }
        }
        
    }
}
