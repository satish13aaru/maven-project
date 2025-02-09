pipeline {
    agent any

    stages {
        stage('SCM Checkout') {
            steps {
                git 'https://github.com/satish13aaru/maven-project.git'
            }
        }
        stage('Validate') {
            steps {
                withMaven(globalMavenSettingsConfig: '', jdk: 'JAVA_HOME', maven: 'MVN_HOME', mavenSettingsConfig: '', traceability: true) {
                sh 'mvn validate'
}
            }
        }
        stage('Compile') {
            steps {
                withMaven(globalMavenSettingsConfig: '', jdk: 'JAVA_HOME', maven: 'MVN_HOME', mavenSettingsConfig: '', traceability: true) {
                sh 'mvn validate'
}
            }
        }
        stage('Build Package') {
            steps {
                withMaven(globalMavenSettingsConfig: '', jdk: 'JAVA_HOME', maven: 'MVN_HOME', mavenSettingsConfig: '', traceability: true) {
                sh 'mvn clean package'
}
            }
        }
        //CD Part
        stage('Deploy') {
            steps {
                sshagent(['DEVCICD']) {
                sh 'scp -o StrictHostKeyChecking=no webapp/target/webapp.war ec2-user@172.31.9.94:/usr/share/tomcat/webapps'
}
}
            }
        }
}
