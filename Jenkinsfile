pipeline {
  agent any
  environment {
    //adding a comment for the commit test
    //DEPLOY_CREDS = credentials('deploy-anypoint-user')
    //ENV_SANDBOX_CREDS = credentials('env-sandbox-user')
    MULE_VERSION = '4.4.0'
    BG = "apisero"
    WORKER = "Micro"
  }
  stages {
    stage('Build') {
      steps {
            bat 'mvn -B -U -e -V clean -DskipTests package'
      }
    }
     stage('Deploy Development') {
      environment {
        ENVIRONMENT = 'Sandbox'
        APP_NAME = 'prc-instant-stockmarket-alert-usecase'
      }
      steps {
            bat 'mvn -U -V -e -B -DskipTests deploy -DmuleDeploy -Dmule.version="%MULE_VERSION%" -Danypoint.username=vijay16112021 -Danypoint.password=Alphaviz@1996 -Dcloudhub.app="%APP_NAME%" -Dcloudhub.environment="%ENVIRONMENT%" -Dcloudhub.bg="%BG%" -Dcloudhub.worker="%WORKER%" -Danypoint.platform.client_id=c5d4f8ba91854890add864c3c926f0ee -Danypoint.platform.client_secret=731649932cE24D278913E89aF81bDE45'
      }
    }
  }
  tools {
    maven 'mvn'
  }
}