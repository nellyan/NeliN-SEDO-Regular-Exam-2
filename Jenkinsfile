pipeline {
    agent {
        label 'windows' // Make sure this agent has .NET 6 installed
    }

    environment {
        DOTNET_VERSION = '6.0.x'
    }

    stages {
        stage('Check Branch') {
            when {
                branch 'main'
            }
            steps {
                echo "Running on main branch"
            }
        }

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Verify .NET SDK') {
            steps {
                bat 'dotnet --version'
            }
        }

        stage('Restore dependencies') {
            steps {
                bat 'dotnet restore'
            }
        }

        stage('Build') {
            steps {
                bat 'dotnet build --no-restore'
            }
        }

        stage('Test') {
            steps {
                bat 'dotnet test --no-build --verbosity normal'
            }
        }
    }
}
