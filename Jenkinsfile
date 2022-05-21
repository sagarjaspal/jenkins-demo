def inputMap = [:]
def envList = ['./dev/','./sit/']

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
                    def allFilePathString = sh (
                        script : 'find . -name *.cer',
                        returnStdout : true
                    )
                    echo "Files : ${allFilePathString}"
                    def allFilePathList = allFilePathString.split('\n')

                    for(String envItem in envList) {
                        def envMap = [:]
                        for(String filePath in allFilePathList) {
                            if (filePath.matches("${envItem}(.*)")) {
                                String shortFilePath = filePath.minus(envItem)
                                int delim = shortFilePath.indexOf('/')
                                String aliasName = shortFilePath.substring(0,delim)
                                String fileName = shortFilePath.substring(delim+1)

                                envMap.put(aliasName, fileName)
                            }
                        }
                        inputMap.put(envItem, envMap)
                    }

                    echo "${inputMap}"
                }
            }
        }
    }
}
