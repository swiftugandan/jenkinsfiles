def props
pipeline {
    agent any
    environment {
        CI = 'true'
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
                    def PWD = increment_version("1.0.0", "release")
                    echo "PWD = ${PWD}"
                }
            }
        }
    }
}

def increment_version(semver, level) {
    return sh (script: '''#!/bin/bash
        echo "$semver $level"
        IFS='.' read -ra ver <<< "$semver"
        [[ "${#ver[@]}" -ne 3 ]] && echo "Invalid semver string" && return 1

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
    ''',
    returnStdout: true
    ).trim()
}