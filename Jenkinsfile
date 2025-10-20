properties([
    pipelineTriggers([
        githubPush()
    ])
])

node {  
    stage('Preparation') {
        catchError(buildResult: 'SUCCESS') {
            sh 'docker stop samplerunning'
            sh 'docker rm samplerunning'
        }
    }
    stage('Build') {
        build job: 'BuildSampleApp', propagate: true, wait: true, parameters: [], quietPeriod: 0
    }
    stage('Results') {
        build job: 'TestSampleApp', propagate: true, wait: true, parameters: [], quietPeriod: 0
    }
}
