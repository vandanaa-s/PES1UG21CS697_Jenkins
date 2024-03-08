pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                script {
                    // Compile the new_file.cpp using shell script
                    //sh 'g++ -o new_file new_file.cpp'
                    // Introduce an intentional error by providing a wrong file name
                    sh 'g++ -o new_file new_file_wrong_name.cpp'
                    // Trigger the 'PES1UG21CS202-1' Jenkins job for building
                    build 'PES1UG21CS697-1'
                }
            }
        }

        stage('Test') {
            steps {
                script {
                    // Run the executable of the compiled C++ file
                    sh './new_file'
                }
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploy'
            }
        }
    }

    post {
        always {
            echo 'Pipeline completed'
        }
        failure {
            echo 'Pipeline failed'
        }
    }
}
