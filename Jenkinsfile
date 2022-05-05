pipeline {

    agent any

    environment {
        GIT_BRANCH = "${GIT_BRANCH}"
    }

    stages {

        stage ('Set1') {
            steps {
                script {
                    GCP_PROJECT_ID = "sample_project"   
                    ENVIRONMENT = "dev"  
                    BUCKET = "gs://"
                }
            }
        }

        stage ("Sync") {
            steps {
                script {
                    sh '''#!/bin/bash
                     gsutil -m rsync -d -r -x "^reports_(\\d+)\\.py$" $(env.SCRIPT_LOC)/  ${GIT_BRANCH}/dags/
                    '''
                }
            }
        }

    }

}