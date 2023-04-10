// jenkinsfile for multi branch configuration

pipeline{
    agent any
    environment{
        githubcreds = credentials('GITHUB-CRED')
    }
    parameters {string(name : "VERSION", defaultValue : "1.3-Beta", trim : false, description : "Dummy version number")}
    stages{
        stage("cloning git repo"){
            steps{
                git branch: 'main', credentialsId: 'GITHUB-CRED', url: 'https://github.com/PratikKumar125/kubernetes-mongodb-statefulset.git'
                bat "git log --pretty=oneline"  
            }
        }
        stage("building"){
            steps{
                if (env.BRANCH_NAME == "main"){
                    bat "echo building your code ${params.VERSION} ${githubcreds_USR} sir"
                } 
                else{
                    echo "no build available for ${env.BRANCH_NAME}"
                }              
            }
        }
        stage("pushing back to the git"){
            steps{
                echo "test done for ${env.BRANCH_NAME}"
            }
        }
    }
}
