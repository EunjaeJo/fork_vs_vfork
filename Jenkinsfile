node {
    def app
    stage('Clone repository') {
        git 'https://github.com/ejJo-sungshin/fork_vs_vfork.git'
    }
    stage('Build image') {
        app = docker.build("jaeae/test")
    }
    stage('Test image') {
        app.inside {
            sh 'make test'
        }
    }
    stage('Push image') {
        docker.withRegistry('https://index.docker.io/v1/', 'jaeae') {
           app.push("${env.BUILD_NUMBER}")
           app.push("latest")
        }
    }
}
