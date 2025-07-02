
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
            choices: ['dev', 'test', 'stage', 'prod'],
            description: 'Select The en to ENVIRONMENT to Deploy'
        )
    }
    agent any
    stages {
// Parallel Stage
        stage('Parallel Stage') {
            parallel{
            //Stage Build
                    stage('Build') {
                        steps {
                            echo 'Building DSOC3 Web-APP..'
                        }
                    } //EO Stage Build
            //Stage Test
                    stage('Test') {
                        steps {
                            echo 'Testing DSOC3 Web-APP..'
                            echo "GIT_BRANCH: ${GIT_BRANCH}"
                        }
                    } //EO Stage Test
            } //EO parallel Block
        } //EO Parallel Stage
//Stage Deploy
        stage('Deploy') {
        //WHEN Block
            when {
               // branch 'origin/test1'
               expression {
                //return env.GIT_BRANCH == 'origin/test1'
                return params.BRANCH == 'test' &&  params.ENVIRONMENT == 'stage'
               }
            }
            steps {
                echo 'Deploying DSOC3 Web-APP..'
                
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
