pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                git 'https://github.com/wrpsj2004/E-Commerce-FE-Homepage'
                bat "npm install"
            }
        }

        stage('Scan') {
            steps {
withSonarQubeEnv('sq1') {
  script {
    def scannerHome = tool name: 'SonarScanner', type: 'hudson.plugins.sonar.SonarRunnerInstallation'
    bat """
      "${scannerHome}\\bin\\sonar-scanner.bat" ^
        -Dsonar.projectKey=mywebapp ^
        -Dsonar.projectName="mywebapp" ^
        -Dsonar.sources=. ^
        -Dsonar.sourceEncoding=UTF-8 ^
        -Dsonar.exclusions=node_modules/**,build/**,dist/**,**/*.spec.*,**/*.test.*
    """
  }
}
            }
        }
    }
}
