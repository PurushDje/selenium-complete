pipeline{

    agent any
    stages{
        stage('Package Test Project'){
            steps{
                bat "mvn clean package -DskipTests"
            }

        }
        stage('Build Image'){
            steps{
                bat "docker build -t=djearamalu/seldoc ."
            }

        }

        stage('Push Image'){
            environment{
                DOCKER_HUB= credentials('seldoc')
            }
            steps{
                bat 'docker login -u %DOCKER_HUB_USR% -p %DOCKER_HUB_PSW%'
                bat "docker push djearamalu/seldoc"
            }
        }
    }
    post{
        always{
            bat "docker logout"
        }
    }


}