 pipeline {
    agent {label "docker"}
    stages {
        stage('Gitgaurdian') {
            environment {
                GITGUARDIAN_API_KEY = credentials('gitgaudian-ravi-token')
            }
            steps {
                withDockerContainer(args: "-i --entrypoint=''", image: 'gitguardian/ggshield:latest') {
                    sh "ggshield --version"
                    sh 'ggshield secret scan ci'
                }
            }
        }
    }
}