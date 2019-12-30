node {
    environment {
//        QUAY_PASS = credentials('albertvo15')
        QUAY_PASS = "test"
    }
    checkout scm
    def dockerImage
    stage('start') {
        echo "${env.QUAY_PASS}"
    }
    
    stage('save-env') {
        sh 'env > properties'
    }

    stage('build-image') {
//        sh 'docker build -t $IMAGE_REPO:$IMAGE_TAG .'
        dockerImage = docker.build( "quay.io/albertvo15/test:v4.0.0")
//        sh 'docker build -t albertvo/test:v4.0.0 .'
    }

    stage('tag-image') {
//        sh 'docker tag albertvo/test:v4.0.0 albertvo/test:v4.0.0'
        sh 'docker tag quay.io/albertvo15/test:v4.0.0 quay.io/albertvo15/test:v4.0.0'
//        sh 'docker tag albertvo/test:v4.0.0 albertvo/test:v4.0.0'
//        sh 'docker tag albertvo/test:v4.0.0 albertvo15/test:v4.0.0'
    }
    stage('Deploy Image') {
        echo "${env.QUAY_PASS}"
          docker.withRegistry( 'https://quay.io', 'albertvo15' ) {
            try {
              dockerImage.push()
            } finally {
              echo "PUSH Failed"
            }
          }
    }   
    
    archiveArtifacts 'properties'
}
