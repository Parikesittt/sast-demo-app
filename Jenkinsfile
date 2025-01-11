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
       sh 'python3 -m bandit -f xml -o bandit-output.xml -r . || true'
       recordIssues tools: [sarif(pattern: 'bandit-output.xml')]
     }
   }
  }
}
