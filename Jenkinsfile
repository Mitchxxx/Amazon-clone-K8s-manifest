node {
    def app
    
    env.IMAGE = 'mitchxxx/amazon'

    stage('Clone Repository'){
        git branch: 'main', url : 'https://github.com/Mitchxxx/Amazon-clone-K8s-manifest.git'
    }

    stage('Update Deployment Manifest') {
        script{
            cathError(buildResult: 'SUCCESS', stageResult: 'FAILURE') {
                withCredentials([usernamePassword(credentialsId: 'github-Mitchel', passwdordVariable: 'GIT_PASSWORD', usernameVariable: 'GIT_USERNAME')]) {
                    sh "git config user.email megboko@gmail.com"
                    sh "git config user.name Mitchxxx"
                    sh "cat deployment.yml"
                    sh "sed -i 's+${IMAGE}.*+${IMAGE}:${DOCKERTAG}+g' deployment.yml"
                    sh "cat deployment.yml"
                    sh "git add ."
                    sh "git commit -m 'Done by Jenkins Job updateManifest: ${env.BUILD_NUMBER}'"
                    sh "git push https://${GIT_USERNAME}:${GIT_PASSWORD}@github.com/${GIT_USERNAME}/Amazon-clone-K8s-manifest.git HEAD:main"
                }
            }
        }
    }
}