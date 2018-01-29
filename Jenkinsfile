node {
     docker.withRegistry('https://registry.hub.docker.com', 'docker-hub-credentials') {
     
         git url: "https://github.com/jpaul756/hellonode", credentialsId: 'github-id'
     
         sh "git rev-parse HEAD > .git/commit-id"
         def commit_id = readFile('.git/commit-id').trim()
         println commit_id
     
         stage "build"
         def app = docker.build "jp756/hellonode"
         stage "publish"
         app.push 'master'
         app.push "${commit_id}"
      }
}
