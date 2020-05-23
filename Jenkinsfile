def props
pipeline {
    agent any
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
                    PWD = sh (script: '''#!/bin/bash
                    # $1 - semver string
                    # $2 - level to incr {release,minor,major} - release by default
                    function incr_semver() { 
                        IFS='.' read -ra ver <<< "$1"
                        [[ "${#ver[@]}" -ne 3 ]] && echo "Invalid semver string" && return 1
                        [[ "$#" -eq 1 ]] && level='release' || level=$2

                        release=${ver[2]}
                        minor=${ver[1]}
                        major=${ver[0]}

                        case $level in
                            release)
                                release=$((release+1))
                            ;;
                            minor)
                                release=0
                                minor=$((minor+1))
                            ;;
                            major)
                                release=0
                                minor=0
                                major=$((major+1))
                            ;;
                            *)
                                echo "Invalid level passed"
                                return 2
                        esac
                        echo "$major.$minor.$release"
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