node {
    checkout scm
    def dockerImage
    stage('start') {
        sh 'echo start8'
    }
    
    stage('save-env') {
        sh 'env > properties'
    }

    stage('build-image') {
//        sh 'docker build -t $IMAGE_REPO:$IMAGE_TAG .'
        dockerImage = docker.build( "albertvo15/test:4.0.0")
    }

    stage('tag-image') {
//        sh 'docker tag albertvo/test:v4.0.0 albertvo15/test:v4.0.0'
//        sh 'docker tag albertvo/test:v4.0.0 albertvo/test:v4.0.0'
        sh 'docker tag albertvo15/test:v4.0.0 albertvo15/test:v4.0.0'
    }
    stage('Deploy Image') {
//        docker.withRegistry( '', 'dockerhub' ) {
        docker.withRegistry( 'https://quay.io', 'albertvo15' ) {
          dockerImage.push()
        }
    }   
    
    archiveArtifacts 'properties'
}
