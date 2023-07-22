pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Esta etapa faz o checkout do código-fonte do repositório Git
                checkout scm
            }
        }

        stage('Build') {
            steps {
                // Etapa de construção: instala as dependências e compila o projeto Angular
                sh 'npm install'
                sh 'npm run build'
            }
        }

        stage('Serve') {
            steps {
                // Etapa que executa o servidor da aplicação Angular usando o comando "ng serve"
                sh 'npm run start'
            }
        }

        // Adicione outras etapas conforme necessário, como testes automatizados, implantação, etc.
    }
}
