

pipeline {
// Parameters  Block
    parameters{
        // Strin Input
        string(
            name: 'BRANCH', 
            defaultValue: 'main', 
            description: 'Branch to Deploy'
            )
        // Choice Params
        choice(
            name: 'ENVIRONMENT',
            choices: ['dev', 'test', 'staging', 'prodution'],
            description: 'Select The en to ENVIRONMENT to Deploy'
        )
    } 
    agent { 
        label 'agent-1'
    }
    stages {
            //Stage Build
                    stage('Build') {
                        steps {
                            echo 'Building DSOC3 Web-APP..'
                            sh '''
                            mvn package
                            ls -lrt
                            '''
                        }
                    } //EO Stage Build
            //Stage Test
                    stage('Test') {
                        steps {
                            echo 'Testing DSOC3 Web-APP..'
                            echo "GIT_BRANCH: ${GIT_BRANCH}"
                            
                        }
                    } //EO Stage Test
//Stage Deploy
        stage('Deploy') {
         //WHEN Block
            when {
               // branch 'origin/test1'
               expression {
                //return env.GIT_BRANCH == 'origin/test1'
                return ( params.BRANCH == 'stage' || params.BRANCH == 'prod') &&  ( params.ENVIRONMENT == 'staging' || params.ENVIRONMENT == 'prodution' )
               }
            }
            steps {
                echo 'Deploying DSOC3 Web-APP..'
                sh '''
                sudo cp target/dsoc3-webapp.war /var/lib/tomcat10/webapps/dsoc3-webapp.war
                '''
                
            }
        } //EO Stage Build
    } //EO stages
// POST BLOCK
    post{
        always{
           echo 'This runs ALWAYS' 
        }
        success{
            echo 'This runs ON SUCCESS'
        }
        failure{
            echo 'This runs FAILED!'
        }
    } // EO POST BLOCK
} //EO pipeline
