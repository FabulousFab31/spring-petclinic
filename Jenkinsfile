//pipeline{
stage('build & unit tests') {
    node('build') {
        echo "Build !"
        sleep 5
    }
}

stage('static-analysis') {
    node('build') {
        echo "Static !"
        sleep 5
    }
}
stage('acceptance-tests') {
    parallel chrome: {
        node("build") {
            echo "acceptance - chrome"
        }
    },
            edge: {
                node("build") {
                    echo "acceptance - edge"
                }
            },
            end: {
                node("build") {
                    echo "acceptance - firefox"
                }
            }
}

stage('manual-input') {
    input "T'es sûr tu veux déployer?"
}

