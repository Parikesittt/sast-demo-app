pipeline {
  agent any
  stages {
    stage('Checkout') {
      steps {
        git url: 'https://github.com/Parikesittt/sast-demo-app.git', branch:'master'
      }
    }
   stage('Install Dependencies') {
     steps {
       sh 'pipx install bandit'
     }
   }
   stage('SAST Analysis') {
     steps {
       sh '''
         python3 -m bandit -r . -ll -f txt -o bandit-results.txt || true
          cat bandit-results.txt
       '''
       recordIssues tools: [checkStyle(pattern: 'bandit-results.txt')]
     }
   }
  }
}
