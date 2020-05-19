def props
pipeline {
    agent {
        docker {
            image 'node:6-alpine'
            args '-p 3000:3000'
        }
    }
    environment {
        CI = 'true'
    }
    stages {
        stage('Clone Project Repository') {
            steps {
                sh(label: "Cloning project", script: "git clone https://github.com/swiftugandan/simple-node-js-react-npm-app.git")
            }
        }
        stage('Read Properties') {
            steps {
                dir(simple-node-js-react-npm-app) {
                    script {
                        props = readJSON file: './release-properties.json'
                    }
                }
            }
        }
        stage('Build') {
            dir(simple-node-js-react-npm-app) {
                steps {
                    echo "props.mavenComponents[0]: ${props.mavenComponents[0]}"
                    sh 'npm install'
                }
            }
        }
        stage('Test') {
            dir(simple-node-js-react-npm-app) {
                steps {
                    echo "props.mavenComponents[0]: ${props.mavenComponents[0]}"
                    sh './jenkins/scripts/test.sh'
                }
            }
        }
        stage('Deliver') {
            dir(simple-node-js-react-npm-app) {
                steps {
                    sh './jenkins/scripts/deliver.sh'
                    input message: 'Finished using the web site? (Click "Proceed" to continue)'
                    sh './jenkins/scripts/kill.sh'
                }
            }
        }
    }
}