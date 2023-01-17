pipeline {
    agent any
    
    stages {
        stage('clone from github'){
            steps{
                dir("CI_Jenkins"){
                    echo 'clone git repo'
                    git branch: 'main', changelog: false, poll: false, url: 'https://github.com/Atheros7/JenkinsTP.git'
                    bat 'dir'
                }
            }
        }
        stage('build from github') {
            steps {
                dir("CI_Jenkins"){
                    echo 'pip3 install -r requirements.txt'
                    bat 'pip3 install -r requirements.txt'
                    bat 'python app.py'
                }
            }
        }
        stage('test from github') {
            steps {
                echo 'running test1'
                echo 'running test2'
            }
        }
        stage('deploying from github'){
            steps{
                echo "deployement"
            }
        }
    }
}
