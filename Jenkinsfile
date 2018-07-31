node {
    checkout scm
    def centosImage = docker.build("centos7-systemd", "./centos7/") 

    centosImage.inside {
        sh 'echo Hello World'
    }
}