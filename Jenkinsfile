pipeline{
    agent any
    stages {
        stage ('SCM Connect'){
            steps {
                git changelog: false, url: 'https://github.com/pavansw/simpleMavenJunit.git'
                sh 'echo "SCM Done"'
            }
            
        }
        stage ('Clean and compile'){
            steps {
                sh '''mvn clean
mvn compile'''
            }
        }
        stage ('Test and Package'){
            steps {
                sh '''mvn test
mvn package'''
            }
        }
        stage ('Publish Junit report'){
            steps { 
                junit 'target/surefire-reports/*.xml'
            }
        }  
        stage ('Archive Atifacts'){
            steps {
                archiveArtifacts artifacts: 'target/*.jar', followSymlinks: false
            }
        }
    }
    
}
