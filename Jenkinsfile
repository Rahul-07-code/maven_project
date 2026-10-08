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
            mail to: 'rahulbanoth132@gmail.com',
                 subject: "Jenkins Build Successful",
                 body: "The Jenkins build was successful."
        }

        failure {
            mail to: 'rahulbanoth132@gmail.com',
                 subject: "Jenkins Build Failed",
                 body: "The Jenkins build has failed."
        }
    }
}
