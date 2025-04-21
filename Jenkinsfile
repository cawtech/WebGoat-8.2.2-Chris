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
    -v iq-cli-volume:/nexus-iq \
    -v "${WORKSPACE}":/src \
    openjdk:17 \
      java -jar /nexus-iq/iq-cli.jar \
      -s http://iq:8070 \
      -a admin:admin123 \
      -i WebGoatPOC \
      -t build /src/pom.xml
'''
		
      }
    }
  }
}

