pipeline {
  agent any
  options { timestamps () }

  stages {
    stage('Download retry step') {
      steps {
        timeout(time: 2, unit: 'MINUTES') {
          retry(10) {
            sh """
              sleep 30
              curl https://www.openssl.org/docs/man1.1.1/man1/crl.html | grep "on a CRL by"
            """
          }
        }
          sh """
            echo "Outside retry"
          """
      }
    }
  }
}
