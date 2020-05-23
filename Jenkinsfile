def props
pipeline {
    agent {
        // docker {
        //     image 'node:6-alpine'
        //     args '-p 3000:3000'
        // }
        any
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
                    PWD = sh (script: '''#!/bin/sh
                    function incr_semver() {

                        version=$1

                        IFS='.' read -ra a <<< "$version"
                        if [ ${#a[@]} -ne 3 ]
                        then
                            echo "version format should be major.minor.patch"
                            exit 1
                        fi


                        if [ $2 -eq 'major' ]
                        then
                            ((a[0]++))
                            a[1]=0
                            a[2]=0
                        fi

                        if [ $2 -eq 'minor' ]
                        then
                            ((a[1]++))
                            a[2]=0
                        fi

                        if [ $2 -eq 'patch' ]
                            then
                            ((a[2]++))
                        fi

                        echo "${a[0]}.${a[1]}.${a[2]}"

                    }

                    incr_semver 1.0.0 major
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