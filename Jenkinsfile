pipeline {
    agent any

    stages{
        stage('checkout code'){
            steps {
                git credentialsId: 'pathelloworld' , url : "https://github.com/Riyouk/jenkins_adding_file.git" , branch : 'main'
            }
        }

        stage('install Dependencies'){
            steps {
                bat '''
                    python -m vevn\\Scripts\\activate
                    pip install --upgrade pip
                    pip install -r requirement.txt
                    '''
            }
        }

        stage('run test'){
            steps {
                bat '''
                call venv\\Scripts\\activate
                pytest test.py
                '''
            }
        }
        stage('deploy') {
            steps {
                echo "Deploying application..."

                bat '''
                    call venv\\Scripts\\activate
                    python add.py
                    '''
            }
        }
    }   

    post{
        success {
            echo 'pipeline succeeded'
        }
        failure {
            echo 'pipeline failed'
        }
    }
}