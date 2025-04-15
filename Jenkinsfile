pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                withCredentials([string(credentialsId: 'vault_token', variable: 'vaultkey')]) {
                sh """curl -s --header "X-Vault-Token: $vaultkey" --request GET http://localhost:8200/v1/secret/data/$params.secret | jq .data.data.$params.secret_key""" 
                }
            }
        }
    }
}
