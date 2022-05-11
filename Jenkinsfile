pipeline {
    agent none
    environment {
        DOTNET_CLI_HOME = '/tmp/DOTNET_CLI_HOME'
    }
    stages {
        stage('Back-end - C# code - Build, Test C#'){
            agent{
                docker { image 'mcr.microsoft.com/dotnet/sdk' }
            }
            steps {
                sh 'dotnet build'
                sh 'dotnet test'
            }
        }

        stage('Build and Run TypeScript Code and run linter'){
            agent{
                docker { image 'node:18.1-buster-slim' }
            }
            steps {
                dir('DotnetTemplate.Web'){
                sh 'npm run build'
                sh 'npm t'
                sh 'npm run lint'
                }
            }
        }
    }
}