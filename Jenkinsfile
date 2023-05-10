import com.cloudbees.jenkins.GitHubRepositoryNameContributor;

node {
    stage('Checkout hoppetuba Repo') {
            REPO_DIR = "${env.WORKSPACE}/hoppetuba" 
            
            if (fileExists("${REPO_DIR}")){
                println "Removing old repo"
                sh "rm -rf ${REPO_DIR}"
            } else {
                println "No old repo to delete"
            }
            
            for (Item job : Jenkins.getInstance().getAllItems(Item.class)) {
                print(GitHubRepositoryNameContributor.parseAssociatedNames(job))
            }  
            
            
            println 'Checking out code from Github'
            //["git", "clone", "https://github.com/jannebrunn/hoppetuba/"].execute()
            //GitManager.clone(this, "https://github.com/jannebrunn/hoppetuba.git", "*/gertgibbons", "jenkins");
            sh("git clone  https://jenkins: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@github.com/jannebrunn/hoppetuba/")
            println''
            
            HTML_DIR="${REPO_DIR}/html" 
            println''
        }
    
    stage('Copying files to /var/www/html') {
            println 'Copying files...'
            copyString="cp ${HTML_DIR}/* /var/www/html/"
            sh("${copyString}")
        }

}
