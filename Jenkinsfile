pipeline {
    agent any

    parameters {
        string(name: 'DIRETORIO', description:'Caminho do Diretorio a definir')
    }

    stages {
        stage('Preparação do Ambiente') {
            steps {
                
                echo 'ja instalado'
            }
        }

        stage('Execução do Teste Levenshtein') {
            steps {
                sh 'python3 levenshtein_teste.py'
            }
        }

        stage('Verificação do Arquivo de Perguntas') {
            steps {
                script {
                    if (fileExists('perguntas.txt')) {
                        echo 'Arquivo perguntas.txt encontrado!'
                    } else {
                        error('Arquivo perguntas.txt não encontrado. Interrompendo o pipeline.')
                    }
                }
            }
        }

        stage('Execução do Chatbot') {
            steps {
                sh 'python3 chat_bot.py'
            }
        }
    }
}
