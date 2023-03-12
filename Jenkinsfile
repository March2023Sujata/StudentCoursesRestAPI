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
        stage('deploy to st') {
            steps {
                sh 'kubectl apply -f ./K8s/mysql-aws.yml'
                sh 'kubectl apply -f ./K8s/flask-aws.yml'
                sh 'sleep 10s'
                sh 'kubectl get svc'
            }
        }
    }

}