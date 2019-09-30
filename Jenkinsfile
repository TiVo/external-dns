@Library('tivoPipeline')

emailBreaks {
    node('docker') {
        stage('Code Checkout') {
            checkout scm
        }
        stage('Build Docker Image') {
            docker.withRegistry('https://docker.tivo.com', 'docker-registry') {
                def image = docker.build('docker.tivo.com/external-dns:latest', '--pull .')
                image.push()
            }
        }
    }
}
