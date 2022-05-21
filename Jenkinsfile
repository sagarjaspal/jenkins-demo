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
                def files = sh (
                    script : 'find . -type f -name *.cer'
                    returnStdout : true
                )
                echo "Files : ${files}"
            }
        }
    }
}
