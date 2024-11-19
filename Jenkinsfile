pipeline {
    agent any
    stages {
        stage('Clonar Repositório') {
            steps {
                git branch: 'main', url: 'https://github.com/Badizan/Projeto-flask-ci-cd.git'
            }
        }
        stage('Construir Imagens Docker') {
            steps {
                sh 'docker-compose build'
            }
        }
        stage('Subir Contêineres') {
            steps {
                sh 'docker-compose up -d'
            }
        }
        stage('Testar Aplicação') {
            steps {
                sh '''
                curl -X POST -H "Content-Type: application/json" \
                -d '{"nome":"Teste","sobrenome":"Aluno","turma":"Turma1","disciplinas":"Matemática"}' \
                http://localhost:5000/alunos
                '''
            }
        }
        stage('Desligar Contêineres') {
            steps {
                sh 'docker-compose down'
            }
        }
    }
}

