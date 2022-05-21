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
                        for(String filePath in allFilePathList) {
                            if (filePath.matches("${envItem}(.*)")) {
                                String shortFilePath = filePath.minus(envItem)
                                int delim = shortFilePath.indecOf('/')
                                String aliasName = shortFilePath.substring(0,delim)
                                String fileName = shortFilePath.substring(delim+1)
                                def mapEntry = [:]
                                mapEntry.put(aliasName, fileName)
                                inputMap.put(envItem, mapEntry)

                                echo "${mapEntry}"
                            }
                        }
                    }

                    echo "${inputMap}"
                }
            }
        }
    }
}
