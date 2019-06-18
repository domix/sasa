pipeline {
  agent any
  //Opciones generales del proceso
  options {
    //Si por alguna razón se queda atorado. Se abortara en una hora.
    timeout(time: 1, unit: 'HOURS') 
  }
  stages {
    stage('build') {
      //Puedo establecer variables de ambiente
      environment {
        //AN_ACCESS_KEY = credentials('id-de-la-credencial')
        DEMO_KEY = 'foo_bar'
      }
      steps { 
        withCredentials([[$class: 'FileBinding', credentialsId: 'sasa', variable: 'GOOGLE_APPLICATION_CREDENTIALS']]) {
          sh 'echo "${GOOGLE_APPLICATION_CREDENTIALS}"' // returns ****
          //sh 'gcloud auth activate-service-account --key-file $GOOGLE_APPLICATION_CREDENTIALS'
          sh 'gcloud compute instances list'
        }
      }
    }
  }
}