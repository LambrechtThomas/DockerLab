properties([
    pipelineTriggers([
        githubPush()
    ])
])

node {
    stage('Preparation') {
        catchError(buildResult: 'SUCCESS') {
            sh 'docker stop samplerunning || true'
            sh 'docker rm samplerunning || true'
        }
    }
    stage('Build') {
        build job: 'BuildSampleApp', propagate: true, wait: true
    }
    stage('Results') {
        build job: 'TestSampleApp', propagate: true, wait: true
    }
}
