pipeline {
    agent any

    stages {
        stage('Restore') {
            when {
                anyOf {
                    branch 'main'
                    branch 'feature'
                    branch 'feature/*'
                }
            }
            steps {
                bat 'dotnet restore'
            }
        }

        stage('Build') {
            when {
                anyOf {
                    branch 'main'
                    branch 'feature'
                    branch 'feature/*'
                }
            }
            steps {
                bat 'dotnet build --no-restore'
            }
        }

        stage('Test') {
    when {
        anyOf {
            branch 'main'
            branch 'feature'
            branch 'feature/*'
        }
    }
    steps {
        // Използваме вече инсталирания .NET 10 за тестове
        bat 'dotnet test --no-build --framework net10.0 --verbosity normal'
    }
}
    }
}
