pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'make'
            }
        }
    }

    post {
        success {
            slackSend color: 'good', message: "La build a été effectuée avec succès !"
            emailext (
                to: 'maher.hammouda.ing@gmail.com',
                subject: "Build réussie",
                body: "La dernière build a été effectuée avec succès."
            )
        }

        failure {
            slackSend color: 'danger', message: "La build a échoué !"
            emailext (
                to: 'maher.hammouda.ing@gmail.com',
                subject: "Build échouée",
                body: "La dernière build a échoué. Veuillez vérifier les logs pour plus d'informations."
            )
        }
    }
}