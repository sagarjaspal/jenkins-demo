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
                        script : 'dir /a-D /S /B',
                        returnStdout : true
                    )
                    echo "Files : ${cerFiles}"
                }
            }
        }
    }
}
