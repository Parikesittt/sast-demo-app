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
       bat 'python -m pip install bandit'
     }
   }
   stage('SAST Analysis') {
     steps {
       bat 'python -m bandit -f xml -o bandit-output.xml -r . || exit 0'
       recordIssues tools: [bandit(pattern: 'bandit-output.xml')]
     }
   }
  }
}
