def resetRefSpec(inputSCM, newRefSpec) {
    return [
        $class: 'hudson.plugins.git.UserRemoteConfig',
        url: inputSCM.getUrl(),
        name: inputSCM.getName(),
        refspec: newRefSpec,
        credentialsId: inputSCM.getCredentialsId(),
    ]
}

node {
    stage("Diff to main"){
        echo("Original SCM Remote Config: ${scm.getUserRemoteConfigs().join('\n')}")
        checkout([
            $class: 'GitSCM',
            branches: scm.branches,
            extensions: scm.getExtensions(),
            userRemoteConfigs: [resetRefSpec(scm.getUserRemoteConfigs()[0], '+refs/heads/*:refs/remotes/origin/*')]
        ])
        sh 'git diff --name-only HEAD origin/main'
    }
}
