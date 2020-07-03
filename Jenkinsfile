pipeline {
  agent any
  options { timestamps () }

  stages {
    stage('Download retry step') {
      steps {
        timeout(time: 20, unit: 'SECONDS') {
          retry(2) {
            sh """
              sleep 5
              ! curl https://www.openssl.org/docs/man1.1.1/man1/crl.html | grep "on a CRL by"
            """
          }
        }
      }
      steps {
        sh """
          echo "Outside retry"
        """
      }
    }
  }
}
