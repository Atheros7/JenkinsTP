pipeline {
    agent any
    
    environment {
        def pip = "C:/Users/jeanv/AppData/Local/Programs/Python/Python310/Scripts/pip"
        def python = "C:/Users/jeanv/AppData/Local/Programs/Python/Python310/python"
         
    }
    
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
                    echo 'pip install -r requirements.txt'
                    bat "${pip} install -r requirements.txt"
                }
            }
        }
        stage('test from github') {
            steps {
                dir("CI_Jenkins"){
                    echo "pyhton -m unittest"
                    bat "${python} -m unittest"
                }
            }
        }
        stage('deploying from github'){
            steps{
                dir("CI_Jenkins"){
                    bat 'docker build -t app .'
                    bat 'docker run -dp 5000:5000 app'
                }
            }
        }
    }
}
