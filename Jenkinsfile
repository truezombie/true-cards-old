pipeline {
    agent { label 'master' } 

    stages {
      stage('install') {
          steps {
              dir('api') {
                  sh '''
                      docker run --rm -v \$(pwd):/app -w /app node:14-alpine npm install
                      # docker run --rm -v \$(pwd):/app -w /app node:14-alpine npm run lint
                      # docker run --rm -v \$(pwd):/app -w /app node:14-alpine npm run test
                  '''
              }
              dir('ui') {
                  sh '''
                      docker run --rm -v \$(pwd):/app -w /app node:14-alpine npm install
                      # docker run --rm -v \$(pwd):/app -w /app node:14-alpine npm run lint
                      # docker run --rm -v \$(pwd):/app -w /app node:14-alpine npm run test
                  '''
              }
          }
      }

      stage('deploy') {
          environment {
              DB_USER = credentials('DB_USER')
              DB_PASSWORD = credentials('DB_PASSWORD')
              DB_HOST = credentials('DB_HOST')
              DB_NAME = credentials('DB_NAME')
              DB_PORT = credentials('DB_PORT')
              BCRYPT_ROUND = credentials('BCRYPT_ROUND')
              JWT_SALT = credentials('JWT_SALT')
              JWT_TTL_AUTH_TOKEN = credentials('JWT_TTL_AUTH_TOKEN')
              JWT_TTL_REFRESH_TOKEN = credentials('JWT_TTL_REFRESH_TOKEN')
              EMAIL_ADDRESS = credentials('EMAIL_ADDRESS')
              EMAIL_PASSWORD = credentials('EMAIL_PASSWORD')
              SERVER_PORT = credentials('SERVER_PORT')
          }
          steps {
              sh 'docker-compose --file docker-compose-prod.yml up --build -V --force-recreate -d'
          }
      }
    }
}