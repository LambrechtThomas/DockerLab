node {
    // Automatically trigger this pipeline on each push to GitHub
    properties([
        pipelineTriggers([
            githubPush()
        ])
    ])
    
    stage('Preparation') {
        catchError(buildResult: 'SUCCESS') {
            sh 'docker stop samplerunning'
            sh 'docker rm samplerunning'
        }
    }
    stage('Build') {
        build 'BuildSampleApp'
    }
    stage('Results') {
        build 'TestSampleApp'
    }
}
