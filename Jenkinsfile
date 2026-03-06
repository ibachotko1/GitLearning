pipeline {
    agent any
 
    environment {
        DOTNET_CLI_TELEMETRY_OPTOUT = '1'
    }
 
    stages {
        stage('Restore') {
            steps {
                bat 'dotnet restore FinanceManager.sln'
            }
        }
 
        stage('Build') {
            steps {
                bat 'dotnet build FinanceManager.sln --configuration Release --no-restore'
            }
        }
 
        stage('Test') {
            steps {
                bat 'dotnet test FinanceManager.Tests --configuration Release --no-build --logger trx'
            }
        }
    }
 
    post {
        success {
            echo 'Сборка успешна! Все тесты прошли.'
        }
        failure {
            echo 'Ошибка сборки или тестов. Проверьте последний коммит.'
        }
    }
}
