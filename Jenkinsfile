pipeline {
  agent any

  stages {
    stage('Checkout') {
      steps {
        checkout scm
      }
    }


stage('IQ Scan') {
  steps {
sh '''
  docker run --rm \
    --network poc-env_default \
    -v /home/chris/poc-env/nexus-iq/iq-cli.jar:/nexus-iq/iq-cli.jar \
    -v "${WORKSPACE}":/src \
    openjdk:17 \
      bash -c "echo --- /src contents --- && ls -la /src && echo --- all files --- && find /src || true"
'''
		
      }
    }
  }
}

