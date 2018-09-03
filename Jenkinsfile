pipeline {
    agent any
    
    // parameters { 
    //      string(name: 'tomcat_dev', defaultValue: '35.166.210.154', description: 'Staging Server')
    //      string(name: 'tomcat_prod', defaultValue: '34.209.233.6', description: 'Production Server')
    // } 

    triggers {
         pollSCM('* * * * *') // Polling Source Control
     }

stages{
        stage('Build'){
            steps {
                sh 'mvn clean package'
            }
            post {
                success {
                    echo 'Now Archiving...'
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }

        // stage ('Deploy to Staging'){
        //     steps{
        //         build job: 'Deploy-to-staging'
        //     }
        // }

        // stage ('Deploy to Production'){
        //     steps{
        //         timeout(time:5, unit:'DAYS'){
        //             input message:'Approved PRODUCTION Deployment?'
        //         }

        //         build job: 'Deploy-to-Prod'
        //     }
        //     post{
        //         success {
        //             echo 'Code deployed to Production.'
        //         }
                
        //         failure {
        //             echo ' Deployment Failed.'
        //         }
        //     }
        // }
    }
}