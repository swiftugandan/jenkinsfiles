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
                //sh(label: "Cloning project", script: "git clone https://github.com/swiftugandan/simple-node-js-react-npm-app.git")
                script {
                    echo sh(script: 'pwd', , returnStdout: true).trim()
                    dir("../") {
                        echo sh(script: 'pwd', , returnStdout: true).trim()
                        dir("Testing_the_Solution_master"){
                            echo sh(script: 'pwd', , returnStdout: true).trim()
                        }
                    }
                    echo sh(script: 'pwd', , returnStdout: true).trim()
                }
                script {
                    PWD = sh (script: '''
                    function incr_semver() { 
                        echo "The param is $1"
                    }

                    incr_semver 1.0.0
                    ''',
                    returnStdout: true
                    ).trim()

                    echo "PWD = ${PWD}"
                }
            }


        }
        // stage('Read Properties') {
        //     steps {
        //         script {
        //             dir(simple-node-js-react-npm-app) {
        //                 props = readJSON file: './release-properties.json'
        //             }
        //         }
        //     }
        // }
        // stage('Build') {
        //     steps {
        //         dir(simple-node-js-react-npm-app) {
        //             echo "props.mavenComponents[0]: ${props.mavenComponents[0]}"
        //             sh 'npm install'
        //         }
        //     }
        // }
        // stage('Test') {
        //     steps {
        //         dir(simple-node-js-react-npm-app) {
        //             echo "props.mavenComponents[0]: ${props.mavenComponents[0]}"
        //             sh './jenkins/scripts/test.sh'
        //         }
        //     }
        // }
        // stage('Deliver') {
        //     steps {dir(simple-node-js-react-npm-app) {
        //         sh './jenkins/scripts/deliver.sh'
        //             input message: 'Finished using the web site? (Click "Proceed" to continue)'
        //             sh './jenkins/scripts/kill.sh'
        //         }
        //     }
        // }
    }
}