node("docker") {
    docker.withRegistry('https://hub.docker.com/r/avinasht/docker-build/', 'docker') {
    
        git url: "https://github.com/avinash-fissionhq/docker-build.git", credentialsId: 'avinash-git'
    
        sh "git rev-parse HEAD > .git/commit-id"
        def commit_id = readFile('.git/commit-id').trim()
        println commit_id
    
        stage "build"
        def app = docker.build "docker-build-test"
    
        stage "publish"
        app.push 'master'
        app.push "${commit_id}"
    }
}
