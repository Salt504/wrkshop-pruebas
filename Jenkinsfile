podTemplate(yaml: """
apiVersion: v1
kind: Pod
spec:
  container:
  - name: eclipse
    image: eclipse-temurin:17.0.3_7-jdk
    ttyEnabled: true
    args: --network ci --mount type=volume,source=ci-maven-home,target=/root/.m2
    env:
      - name: ORG_NAME 
        value: 'deors'
      - name: APP_NAME 
        value: 'workshop-pipelines'
      - name: APP_CONTEXT_ROOT 
        value: '/'
      - name: APP_LISTENING_PORT 
        value: '8080'
      - name: TEST_CONTAINER_NAME 
        value: "ci-${env.APP_NAME}-${BUILD_NUMBER}"
      - name: DOCKER_HUB
        value: credentials("${env.ORG_NAME}-docker-hub")
"""
){

     node(POD_LABEL) {
        container('eclipse') {
                echo '-=- compiling project -=-'
//                  sh './mvnw clean compile'
                    sh 'echo "hola"'
            }
        }
    
    
    
//     node(POD_LABEL) {
//        container('eclipse') {
//                echo '-=- execute unit tests -=-'
//                sh './mvnw test org.jacoco:jacoco-maven-plugin:report'
//                junit 'target/surefire-reports/*.xml'
//                jacoco execPattern: 'target/jacoco.exec'
//            }
//        }
//        
//    
//    node(POD_LABEL) {
//        container('eclipse') {
//                echo '-=- execute mutation tests -=-'
//                sh './mvnw org.pitest:pitest-maven:mutationCoverage'
//            }
//        }
//    }
//    
//    node(POD_LABEL) {
//        container('eclipse') {
//                echo '-=- packaging project -=-'
//                sh './mvnw package -DskipTests'
//                archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
//            }
//        }
//        
//    
//    node(POD_LABEL) {
//        container('eclipse') {
//                echo '-=- build Docker image -=-'
//                sh './mvnw docker:build'
//           }
//        }
//        
//        
//    node(POD_LABEL) {
//        container('eclipse') {
//                echo '-=- run Docker image -=-'
//                sh "docker run --name ${env.TEST_CONTAINER_NAME} --detach --rm --network ci --expose ${env.APP_LISTENING_PORT} --expose 6300 --env JAVA_OPTS='-Dserver.port=${env.APP_LISTENING_PORT} -Dspring.profiles.active=ci -javaagent:/jacocoagent.jar=output=tcpserver,address=*,port=6300' ${env.ORG_NAME}/${env.APP_NAME}:latest"
//            }    
//        }    
//        
//    
//    node(POD_LABEL) {
//        container('eclipse') {
//                echo '-=- execute integration tests -=-'
//                sh "curl --retry 5 --retry-connrefused --connect-timeout 5 --max-time 5 http://${env.TEST_CONTAINER_NAME}:${env.APP_LISTENING_PORT}/${env.APP_CONTEXT_ROOT}/actuator/health"
//                sh "./mvnw failsafe:integration-test failsafe:verify -DargLine=\"-Dtest.target.server.url=http://${env.TEST_CONTAINER_NAME}:${env.APP_LISTENING_PORT}/${env.APP_CONTEXT_ROOT}\""
//                sh "java -jar target/dependency/jacococli.jar dump --address ${env.TEST_CONTAINER_NAME} --port 6300 --destfile target/jacoco-it.exec"
//                sh 'mkdir target/site/jacoco-it'
//            }
//        }
//        
//    
//    node(POD_LABEL) {
//        container('eclipse') {
//                echo '-=- execute performance tests -=-'
//                sh "./mvnw jmeter:configure@configuration jmeter:jmeter jmeter:results -Djmeter.target.host=${TEST_CONTAINER_NAME} -Djmeter.target.port=${APP_LISTENING_PORT} -Djmeter.target.root=${APP_CONTEXT_ROOT}"
//                perfReport sourceDataFiles: 'target/jmeter/results/*.csv'
//                sh 'java -jar target/dependency/jacococli.jar report target/jacoco-it.exec --classfiles target/classes --xml target/site/jacoco-it/jacoco.xml'
//                junit 'target/failsafe-reports/*.xml'
//                jacoco execPattern: 'target/jacoco-it.exec'
//        }    
    }