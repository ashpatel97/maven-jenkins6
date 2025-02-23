pipeline {

    agent any

    tools {

        maven 'maven3'

        jdk 'java17'

    }

    stages {

        stage('Download Code from git') {

            steps {

                echo 'Downloading code from Git'

                git branch: 'main', url: 'https://github.com/devopstechlab/maven-jenkins6.git'

            }

        }

        stage('Build') {

            steps {

                echo 'Building Java project using maven'

                sh 'mvn clean package'

            }

        }

        stage('Archive Artifacts') {

            steps {

                echo 'Archiving the artifacts'

                archiveArtifacts artifacts: '**/*.war', followSymlinks: false

            }

        }

        stage('Build Pipleline Deploy') {

            steps {

                build wait: false, job: 'pipeline-deploy-java'

            }

        }

    }

}
