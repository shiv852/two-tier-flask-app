
pipeline{
    
    agent any;
    
    stages{
        stage("Code Clone"){
            steps{
               script{
                   clone("https://github.com/shiv852/two-tier-flask-app.git", "master")
               }
            }
        }
        stage("Trivy File System Scan"){
            steps{
               sh "trivy fs . -o results.json"
            }
        }
        
        stage("Build"){
            steps{
                sh "docker build -t two-tier-flask-app ."
            }
            
        }
        stage("Deploy"){
            steps{
                sh "docker compose up -d --build flask-app"
            }
        }
    }
}
