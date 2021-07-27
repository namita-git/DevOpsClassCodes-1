pipeline {
    agent any

    tools {
        // Install the Maven version configured as "M3" and add it to the path.
        maven "mymaven"
        jdk "myjava"
    }

    stages {
        stage('Compile') {
            steps {
                sh "mvn compile"
            }
        }

    stage('CodeReview') {
            steps {
                sh "mvn pmd:pmd"
            }
        }
    stage('UnitTest') {
            steps {
                sh "mvn test"
            }
        }
    stage('MetricCheck') {
            steps {
                sh "mvn cobertura:cobertura -Dcobertura.report.format=xml"
            }
        }
    stage('Package') {
            steps {
                sh "mvn package"
            }
        }
    }
}
