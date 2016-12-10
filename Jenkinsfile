stage 'Build'
node('build-node') {
  sh "echo building"
  stash includes: 'target/*', name: 'built'
}

input 'Continue to deploy stage?'

lock ('deploy-server') {
  stage 'Deploy'
  node('deploy-node') {
    unstash 'built'
    //sh 'scp target/* user@deploy-server:/deploy'
    sh "echo deploying"
  }
}