stage('Build') {
  node('linux') {
    git([url: 'https://github.com/SumTotalSystems/textAngular.git', branch: 'sumt-edits'])
    sh 'npm install && bower install && grunt'
  }
}

try {
  if (env.BRANCH_NAME == "develop" || env.BRANCH_NAME.startsWith('SS') || env.BRANCH_NAME == "sumt-master") {
      build job: 'Foundation Controls (Nightly)/' + "develop", wait: false
  }
} catch(e) {
  echo 'Unable to find the Foundation control branch for downstream building. Not failing the build for this...'
  emailext body: "Unable to find the Foundation control branch for textAngular repository in github. Please view the build information here: ${env.BUILD_URL}",
      from: 'Jenkins CI Server <jenkins-no-reply@sumtotalsystems.com>',
      subject: 'The foundation-controls project build has failed',
	  to: 'SumTotal-DevOps-Build@skillsoft.com'
	  
      throw err
}
