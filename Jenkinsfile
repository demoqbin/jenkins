pipeline {

    agent { 
        label 'master'
    }

    environment {
        GIT_BRANCH = "${GIT_BRANCH}"
    }



    stages {

        stage ('Set') {
            steps {
                script {
                        GCP_PROJECT_ID = "sample_project"   
                        ENVIRONMENT = "dev"  
                        BUCKET = "gs://"
                    }
                }
            }
        }

         stage ("Set") {
            steps {
                script {
                    sh "gcloud auth list"
                }
            }
        }
      
       stage ("Sync") {
        steps {
            script {
                sh '''
                gsutil -m rsync -d -r -x "^reports_(\d+)\.py$" ${env.SCRIPT_LOC}/  ${BUCKET}/dags/
                '''
            }
        }
    }

}
