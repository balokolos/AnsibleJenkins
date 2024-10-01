pipeline {
    agent any
    
    parameters {
        string(name: 'NAMA', defaultValue: 'BALOKOLOS', description: 'Name parameter')
        choice(name: 'AYAH', choices: ['DESTACOURE', 'ZULHILMI', 'BALOKOLOS'], description: 'Choice parameter')
        booleanParam(name: 'SHOW', defaultValue: true, description: 'Boolean parameter')
    }
    
    stages {
        stage('Print Hostname TTTEST') {
            steps {
                echo 'Running: echo $hostname'
                sh 'echo $HOSTNAME'
            }
        }
        
        stage('Run Script') {
            steps {
                echo "Running script with parameters: NAMA=${params.NAMA}, AYAH=${params.AYAH}, SHOW=${params.SHOW}"
                sh "$HOME/script.sh '${params.NAMA}' '${params.AYAH}' '${params.SHOW}'"
            }
        }
        
        stage('Check Java Version') {
            steps {
                echo 'Running: java --version'
                sh 'java --version'
            }
        }

        stage('Manual Approval') {
            steps {
                input message: 'APPROVE?', ok: 'Approve'
            }
        }

        stage('Show Script Content') {
            steps {
                echo 'Running: cat ~/script.sh'
                sh 'cat ~/script.sh'
            }
        }
    }
}
