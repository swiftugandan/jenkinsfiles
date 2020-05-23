def props
pipeline {
    agent any
    environment {
        CI = 'true'
        semver = "1.0.0"
        level = "minor"
    }
    stages {
        stage('Clone Project Repository') {
            steps {
                script {
                    echo sh(script: 'pwd', , returnStdout: true).trim()
                    dir("../") {
                        echo sh(script: 'pwd', , returnStdout: true).trim()
                        dir("Testing_the_Solution_master"){
                            echo sh(script: 'pwd', , returnStdout: true).trim()
                        }
                    }
                    echo sh(script: 'pwd', , returnStdout: true).trim()
                    def PWD = increment_version()
                    echo "PWD = ${PWD}"
                }
            }
        }
    }
}

def increment_version() {
    return sh (script: '''#!/bin/bash
        IFS='.' read -ra ver <<< "$semver"
        [[ "${#ver[@]}" -ne 3 ]] && echo "Invalid semver string" && exit 1

        patch=${ver[2]}
        minor=${ver[1]}
        major=${ver[0]}

        case $level in
            patch)
                patch=$((patch+1))
            ;;
            minor)
                patch=0
                minor=$((minor+1))
            ;;
            major)
                patch=0
                minor=0
                major=$((major+1))
            ;;
            *)
                echo "Invalid level passed"
                exit 2
        esac
        echo "$major.$minor.$patch"
    ''',
    returnStdout: true
    ).trim()
}