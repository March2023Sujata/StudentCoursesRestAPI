pipeline {
    agent { label 'docker' }
    triggers { 
        pollSCM('* 23 * * 1-5')
    }
    stages {
        stage('vcs') {
            steps {
                git url: 'https://github.com/March2023Sujata/StudentCoursesRestAPI.git',
                    branch: 'sprint_1_release'
            }
        }
        stage('build') {
            steps {
                sh 'docker image build -t sujata1984/spc:latest .'
            }
        }
        stage('scan and push') {
            steps {
                sh 'echo docker scan sujata1984/spc:latest'
                sh 'docker image push sujata1984/spc:latest'
            }
        }
    }

}