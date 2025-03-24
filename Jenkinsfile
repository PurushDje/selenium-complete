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
                bat "docker build -t=djearamalu/selenium ."
            }

        }

        stage('Push Image'){
            steps{
                bat "docker push djearamalu/selenium"
            }
        }
    }


}