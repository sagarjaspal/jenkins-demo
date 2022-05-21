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
                    find . -name \*.cer
                }
            }
        }
    }
}
