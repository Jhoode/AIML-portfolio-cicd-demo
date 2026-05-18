pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                echo 'Pulling code from GitHub...'
            }
        }

        stage('Validate HTML Files') {
            steps {
                sh '''
                ls -la
                test -f index.html
                test -f theme.css
                '''
            }
        }

        stage('Deploy to Apache') {
            steps {
                sh '''
                sudo rsync -av --delete ./ /var/www/html/
                sudo systemctl restart apache2
                '''
            }
        }
    }
}
