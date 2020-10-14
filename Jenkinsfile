node {
    def app
    
    stage('Clone repository') {
        git credentialsId: 'bef4316a-ccfa-4c53-92d0-c59a58a54576', url: 'https://github.com/AlekseyZmitrykevich/Spring-Boot-Sample-Project.git'
        sh 'cd /var/lib/jenkins/workspace/maven-build'
        sh 'chmod +x mvnw'
    }
    stage('Build image') {
        AppImage = docker.build("test:${env.BUILD_ID}")
    }
    stage('Push image') {
        docker.withRegistry('https://599278947730.dkr.ecr.eu-central-1.amazonaws.com', 'ecr:eu-central-1:build-ecr') {
            AppImage.push()
        }
    }
}
