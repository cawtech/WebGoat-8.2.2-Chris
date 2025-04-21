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
            -v "$WORKSPACE":/src \
            sonatype/nexus-iq-cli:latest \
              java -jar /opt/nexus-iq-cli.jar \
              -s http://iq:8070 \
              -a admin:admin123 \
              -i WebGoatPOC \
              -t build /src/pom.xml
        '''

      }
    }
  }
}

