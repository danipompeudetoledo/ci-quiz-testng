pipeline {
    agent any

    tools {
        maven 'Maven'        // o nome do Maven configurado no Jenkins (deixe 'Maven' se não alterou)
        jdk 'JDK 24'         // exatamente como aparece na tela de configuração
    }

    stages {
        stage('Checkout') {
            steps {
                echo '📦 Clonando repositório do GitHub...'
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo '🏗️ Executando build do projeto Maven...'
                bat 'mvn clean compile'
            }
        }

        stage('Test') {
            steps {
                echo '🧪 Executando testes com TestNG...'
                bat 'mvn test'
            }
        }
    }

    post {
        success {
            echo '✅ Build e testes executados com sucesso!'
        }
        failure {
            echo '❌ Falha no build ou nos testes!'
        }
    }
}
