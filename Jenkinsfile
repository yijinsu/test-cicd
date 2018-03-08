pipeline {
    agent {
        docker {
            image 'maven:3-alpine'
            args '-v /root/.m2:/root/.m2'
        }
    }
    stages {
        stage('Build') {
            steps {
                sh 'mvn -B -DskipTests clean package'
            }
        }

        stage('Test with JaCoCo') {
                    steps {
                        sh 'mvn test jacoco:report'
                    }

                }
         stage('SonarQube Analysis') {
                             steps {
                                 sh 'mvn sonar:sonar -Dsonar.host.url=http://tbmstoreapp1.qa1.iad2.xaxis.net:8082 -Dsonar.login=2735250784ddff4fc125f2e04a1549ebf1503d69'
                             }

                         }
    }
}

