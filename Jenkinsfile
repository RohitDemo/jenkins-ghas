pipeline {
  agent any
  stages {
    stage('CodeQL Scan') {
      environment {
        GITHUB_CREDS = credentials('pat-that-may-work')
      }
      steps {
        sh '''pwd
ls -lah
commit_id=`git rev-parse HEAD`
echo " COMMIT ID is $commit_id"
refs_value=`git symbolic-ref HEAD`
echo "REF is $refs_value"
/home/ubuntu/codeql-bundle/codeql-runner-linux init --repository rohitdemo/jenkins-ghas --github-url https://github.com --github-auth $GITHUB_CREDS_PSW --codeql-path /home/ubuntu/codeql-bundle/codeql/codeql
/home/ubuntu/codeql-bundle/codeql-runner-linux analyze --repository rohitdemo/jenkins-ghas --github-url https://github.com --github-auth $GITHUB_CREDS_PSW --commit $commit_id --ref $refs_value'''
      }
    }

  }
}