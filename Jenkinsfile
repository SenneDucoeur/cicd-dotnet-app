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
    stage('Deploy') {
        // Stop the old application process if it is running
        sh 'pkill -f "dotnet run" || true'
        
        // Start the new compiled application in the background and prevent Jenkins from killing it
        sh 'JENKINS_NODE_COOKIE=dontKillMe nohup dotnet run --project src/Rise.Server/Rise.Server.csproj --urls "http://0.0.0.0:5000" > app.log 2>&1 &'
    }
}