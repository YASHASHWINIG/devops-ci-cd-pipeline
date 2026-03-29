pipeline {
    agent any

    tools {
        jdk 'JAVA_HOME'
        maven 'MAVEN_HOME'
    }

    stages {

        stage('Cloning spring petclinic repository') {
            steps {
                git branch: 'main', url: 'https://github.com/YASHASHWINIG/spring-framework-petclinic.git'
            }
        }

        stage('Compiling the src code of spring petclinic application') {
            steps {
                sh 'mvn compile'
            }
        }

        stage('Testing the src code of spring petclinic application') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Analyzing source code via Sonarqube') {
            steps {
                withSonarQubeEnv('Sonarqube') {
                    sh 'mvn verify sonar:sonar -Dsonar.projectName=spring-petclinic -Dsonar.projectKey=spring-petclinic'
                }
            }
        }

        stage('Deploying build into nexus repository') {
            steps {
                withMaven(globalMavenSettingsConfig: 'nexus-config', jdk: 'JAVA_HOME', maven: 'MAVEN_HOME', traceability: true) {
                    sh 'mvn clean deploy'
                }
            }
        }

        stage('Deploying build in tomcat server') {
            steps {
                sshagent(['tomcat-credentials']) {
                    sh 'scp -o StrictHostKeyChecking=no target/petclinic.war ubuntu@44.212.19.235:/home/ubuntu/apache-tomcat-10.1.52/webapps/'
                }
            }
        }
    }

    post {
        success {
            mail to: 'yashashwinig2003@gmail.com',
                 subject: 'Build Success',
                 body: 'WAR build successfully deployed into Tomcat server'
        }

        failure {
            mail to: 'yashu1903@gmail.com',
                 subject: 'Build Failed',
                 body: 'Build failed. Please check Jenkins.'
        }
    }
}
