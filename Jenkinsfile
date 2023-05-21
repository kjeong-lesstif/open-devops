// This shows a simple build wrapper example, using the AnsiColor plugin.
pipeline {
    // This displays colors using the 'xterm' ansi color map.
    //ansiColor('xterm') {
        // Just some echoes to show the ANSI color.
    //    stage "\u001B[31mI'm Red\u001B[0m Now not"
    //}
    
    agent any
    
    stages{
        stage('Build') {
            steps {
                echo 'Clone'
                git branch: 'main',  url: 'https://github.com/kjeong-lesstif/open-devops'
                //credentialsId: 'credentail id',
                
            }
     
           post {
               always {
                   jiraSendBuildInfo site: 'kjeong-demo-1.atlassian.net'
               }
           }
        }
        
        stage('Deploy - Production') {
        //   when {
        //       branch 'master'
        //   }
           steps {
               echo 'Deploying to Production from master...'
           }
           post {
               always {
                   jiraSendDeploymentInfo site: 'kjeong-demo-1.atlassian.net', environmentId: 'us-prod-1', environmentName: 'us-prod-1', environmentType: 'production'
               }
           }
}
    }
}
