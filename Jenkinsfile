pipeline {
    agent any 

    stages {
        stage('Build') { 
            steps { 
                sh 'mvn clean -DskipTest -U package' 
            }
        }
        stage('Test'){
            steps {
                sh 'mvn test pmd:pmd'
                junit 'target/surefire-reports/*.xml' 
                pmd canRunOnFailed: true, pattern: 'target/pmd.xml'
                
            }
        }
        stage('Deploy') {
            steps {
                sh 'mvn -DskipTest deploy'
            }
        }
    }
}
