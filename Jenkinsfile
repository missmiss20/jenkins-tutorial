pipeline {
    agent {
        docker {
            image 'custom_agent_python'
            reuseNode true
        }
    }

    stages {
        stage('Build Docker Image') {
            agent none
            steps {
                script {
                    // Build the Docker image from the Dockerfile
                    docker.build('custom_agent_python', '-f path/to/Dockerfile .')
                }
            }
        }

        stage('Install Requirements') {
            steps {
                echo "Installing Requirements"
                sh 
                '''
                    cd myapp
                    pip install -r requirements.txt
                '''
            }
        }

        stage('Test') {
            steps {
                echo 'Testing'
                sh  
                '''
                    cd myapp
                    python3 hello.py
                    python3 hello.py --name=Brad
                '''
            }
        }

        stage('Deliver') {
            steps {
                echo 'Deliver'
                sh 
                '''
                    echo "doing delivery stuff.."
                '''
            }
        }
    }

    triggers {
        pollSCM('* * * * *')
    }
}
