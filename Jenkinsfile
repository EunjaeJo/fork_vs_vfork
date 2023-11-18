node {
    def app
    stage('Clone repository') {
        git 'https://github.com/ejJo-sungshin/fork_vs_vfork.git'
    }
    stage('Build image') {
        app = docker.build("EunjaeJo/prbasedtest")
    }
    stage('Test image') {
        app.inside {
            sh 'make test'
        }
    }
    stage('Push image') {
        docker.withRegistry('https://registry.hub.docker.com', 'EunjaeJo') {
           app.push("${env.BUILD_NUMBER}")
           app.push("latest")
        }
    }
}
