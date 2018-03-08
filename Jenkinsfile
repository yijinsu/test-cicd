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
                                 sh 'mvn sonar:sonar -Dsonar.host.url=http://192.168.99.100:9000 -Dsonar.login=54ff0fbaa83de0c840dddd0716871808807e5bfd'
                             }

                         }
    }
}

