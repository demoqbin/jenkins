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
                    script {
                        if (env.GIT_BRANCH != 'origin/main') {
                            sh '''#!/bin/bash
                            gsutil -m rsync -d -r -x "^reports_(\\d+)\\.py$" ${SCRIPT_LOC}/  ${GIT_BRANCH}/dags/
                            '''
                        } else {
                            echo ${GIT_BRANCH}
                        }
                }
            }
        }

    }

}
}