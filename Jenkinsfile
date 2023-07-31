pipeline {
    agent { label 'MAVEN_JDK' }
    stages {
        stage('vcs') {
            steps {
                git url: 'https://github.com/2023August/game-of-life.git',
                    branch: 'declarative'
            }
        }
        stage('package') {
            tools { jdk 'JAVA_8_UBUNTU'}
            steps {
                sh 'mvn package'
                sh 'mvn clean'
            }
        }
        stage('post build') {
            steps {
                archiveArtifacts artifacts: '**/target/gameoflife.war',
                                 onlyIfSuccessful: true
                junit testResults: '**/TEST-*.xml'                 
            }
        }
    }
}