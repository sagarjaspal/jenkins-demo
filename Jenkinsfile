pipeline {
    agent any

    stages {
        stage ("Say Hello") {
            steps {
                script {
                    echo "Hello Jenkins"
                }
            }
        }
        stage ("Find Cer") {
            steps {
                script {
                    def cerFiles = sh (
                        script : 'find . -type f -name *.cer',
                        returnStdout : true
                    )
                    echo "Files : ${cerFiles}"
                }
            }
        }
    }
}
