pipeline {
    agent {
        kubernetes {
            label 'pod-eclipse'
            containerTemplate {
                name 'contenedor-eclipse'
                image 'eclipse-temurin:17.0.3_7-jdk'
                ttyEnabled true
                args '--network ci --mount type=volume,source=ci-maven-home,target=/root/.m2'
            }
        }
    }

    environment {
        ORG_NAME = 'deors'
        APP_NAME = 'workshop-pipelines'
        APP_CONTEXT_ROOT = '/'
        APP_LISTENING_PORT = '8080'
        TEST_CONTAINER_NAME = "ci-${APP_NAME}-${BUILD_NUMBER}"
        DOCKER_HUB = credentials("${ORG_NAME}-docker-hub")
    }
    stages {
            stage('Compile') {
                steps {
                    container('pod-eclipse') {
                        echo '-=- compiling project -=-'
                        sh './mvnw clean compile'
                    }
                }
            }
    }
}