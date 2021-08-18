node {
    checkout scm
    stage("Diff to main"){
        echo("Original SCM Remote Config: ${scm.getUserRemoteConfigs().join('\n')}")
        sh 'git diff --name-only HEAD origin/main'
    }
}
