node {
    checkout scm
    step("Diff to main"){
        echo("Hello World!")
        sh 'git diff --name-only HEAD main'
    }
}
