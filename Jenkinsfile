node {
    stage('Checkout') {
        checkout scm
    }
    stage('Restore') {
        sh 'dotnet restore Rise.sln'
    }
    stage('Build') {
        sh 'dotnet build Rise.sln --configuration Release --no-restore'
    }
    stage('Test') {
        sh 'dotnet test Rise.sln --configuration Release --no-build'
    }
}