
pipeline {
// Parameters  Block
    parameters{
        string(name: 'BRANCH', defaultValue: 'main', description: 'Branch to Deploy')
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
                return params.BRANCH == 'test'
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
