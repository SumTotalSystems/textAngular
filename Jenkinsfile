stage('Build') {
  node('master') {
    git([url: 'https://github.com/SumTotalSystems/textAngular.git', branch: 'sumt-edits'])
    sh 'npm install && bower install && grunt'
  }
}

milestone 1
