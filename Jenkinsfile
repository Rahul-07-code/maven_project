pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                echo 'Hello World - Webhook test1'
            }
        }
    }

    post {
        success {
            mail to: 'marouthu.bc@gmail.com',
                 subject: "Jenkins Build Successful",
                 body: "The Jenkins build was successful."
        }

        failure {
            mail to: 'marouthu.bc@gmail.com',
                 subject: "Jenkins Build Failed",
                 body: "The Jenkins build has failed."
        }
    }
}
