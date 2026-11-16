pipeline {
    agent any

    stages {
        stage('Hello 1') {
            steps {
                echo 'Hello World'
            }
        }

        stage('Hello3') {
            steps {
                echo 'Hello 3'
            }
        }
    }
}

pipeline {
    agent any
    tools{
        maven 'MAVEN-HOME'
    }
    stages {
        stage('git repo & clean') {
            steps {
                //bat "rmdir  /s /q mavenjava"
                bat "git clone provide your github link"
                bat "mvn clean -f mavenjava"
            }
        }
        stage('install') {
            steps {
                bat "mvn install -f mavenjava" #project name#
            }
        }
        stage('test') {
            steps {
                bat "mvn test -f mavenjava"
            }
        }
        stage('package') {
            steps {
                bat "mvn package -f mavenjava"
            }
        }

# Use an official Java runtime as a parent image
FROM tomcat:9-jdk11

# Copy the built WAR file to the Tomcat webapps directory
COPY target/*.war /usr/local/tomcat/webapps/

# Expose the port Tomcat is running on
EXPOSE 8080

# Start Tomcat server
CMD ["catalina.sh", "run"]


services:
  web:
    image: nginx:latest
    ports:
      - "8080:80"
    depends_on:
      - redis

  db:
    image: postgres:15
    environment:
      POSTGRES_USER: demo
      POSTGRES_PASSWORD: demo
      POSTGRES_DB: demo_db
    volumes:
      - db-data:/var/lib/postgresql/data
    networks:
      - app-net

  redis:
    image: redis:alpine

networks:
  app-net:

volumes:
  db-data:

    }
}
