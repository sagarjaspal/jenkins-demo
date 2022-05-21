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
                        script : 'find . -name *.cer',
                        returnStdout : true
                    )
                    echo "Files : ${cerFiles}"
                }
            }
        }
    }
}
