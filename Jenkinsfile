pipeline {
  agent any

  stages {
    stage('Checkout') {
      steps {
        checkout scm
      }
    }


/*
stage('IQ Scan') {
  steps {
    // 🔍 Temporary debug: show contents of /src inside the container
    sh '''
      echo "🔍 Inspecting container mount"
      docker run --rm \
        --network poc-env_default \
        -v "${WORKSPACE}":/src \
        openjdk:17 \
          ls -la /src
    '''

    // Actual scan
        sh '''
          docker run --rm \
            --network poc-env_default \
            -v /home/chris/poc-env/iq-cli.jar:/tools/iq-cli.jar \
            -v "${WORKSPACE}":/src \
            openjdk:17 \
              java -jar /tools/iq-cli.jar \
              -s http://iq:8070 \
              -a admin:admin123 \
              -i WebGoatPOC \
              -t build /src/pom.xml
        '''
*/

stage('IQ Scan') {
  steps {
    sh '''
      docker run --rm \
        --network poc-env_default \
        -v /home/chris/poc-env/iq-cli.jar:/tools/iq-cli.jar \
        -v "${WORKSPACE}":/src \
        openjdk:17 \
          bash -c "echo 🔍 CONTENTS OF /src && ls -la /src && echo 🔍 RECURSIVE FILE SEARCH && find /src"
    '''

      }
    }
  }
}

