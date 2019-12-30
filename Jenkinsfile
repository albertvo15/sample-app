pipeline {
    environment {
//        QUAY_PASS = credentials('albertvo15')
        QUAY_PASS = "test"
    }
    checkout scm
    def dockerImage
    stage('start') {
        echo "${env.QUAY_PASS} 2"
    }
    
    stage('save-env') {
        sh 'env > properties'
    }

    stage('build-image') {
//        sh 'docker build -t $IMAGE_REPO:$IMAGE_TAG .'
//        dockerImage = docker.build( "albertvo/test:v4.0.0")
        sh 'docker build -t albertvo/test:v4.0.0 .'
    }

    stage('tag-image') {
        sh 'docker tag albertvo/test:v4.0.0 albertvo/test:v4.0.0'
//        sh 'docker tag albertvo/test:v4.0.0 albertvo15/test:v4.0.0'
//        sh 'docker tag albertvo/test:v4.0.0 albertvo/test:v4.0.0'
//        sh 'docker tag albertvo/test:v4.0.0 albertvo15/test:v4.0.0'
    }
    stage('Deploy Image') {
        steps {
        echo "${env.QUAY_PASS}"
//          sh "docker login -u=albertvo15 -p=${env.QUAY_PASS} quay.io"
//          sh "docker push quay.io/albertvo15/test:v4.0.0"
//        docker.withRegistry( '', 'dockerhub' ) {
//        docker.withRegistry( 'https://quay.io', 'albertvo15' ) {
//          dockerImage.push('albertvo15/test:v4.0.0')
//          dockerImage.push()
        }
    }   
    
    archiveArtifacts 'properties'
}
