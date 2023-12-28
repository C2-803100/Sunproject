pipeline {
    agent any

    stages {
        stage ('SCM') {
            steps {
                git branch: 'master', url: 'https://github.com/C2-803100/sunproject.git'
            }
        }
        stage ('docker login') {
            steps {
                sh 'echo dckr_pat_lbuI09OFrD6glMS-qu5fRjYzkfY | /usr/bin/docker login -u ankush1996 --password-stdin'
            }
        }
        stage ('docker build image') {
            steps {
                sh '/usr/bin/docker image build -t ankush1996/myhttpd .'
            }
        }
        stage ('docker push image') {
            steps {
                sh '/usr/bin/docker image push ankush1996/myhttpd'
            }
        }
        stage ('docker remove service') {
            steps {
                sh '/usr/bin/docker service rm myservice'
            }
        }
        stage ('docker create service') {
            steps {
                sh '/usr/bin/docker service create --replicas 5 --name myservice -p 9091:80 ankush1996/myhttpd'
            }
        }
    }
} 

