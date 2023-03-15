pipeline {

    agent any
    tools{
       maven 'Maven_Home'  

    }
    stages {
        stage ('GIT') {
            steps {
               echo "Getting Project from Git sss";
                git branch: "master",
                    url: "https://github.com/WafaMayEsprit/kaddem-project.git";
            }
        }

          stage("Test") {
            steps {
                sh "mvn test"
            }
        }

           stage("Sonnar") {
            steps {

                sh "mvn sonar:sonar  \
                -Dsonar.projectKey=sonarname \
                -Dsonar.login=10b16c2667e80e190160dac7e531c5629a5e642d \
                -Dsonar.host.url=http://192.168.43.42:9092/  "


            }
        }

        stage("Build") {
            steps {
                sh "mvn -version"
                sh "mvn clean package -DskipTests"
            }
        }
         stage("NEXUS") {
            steps {

                sh "mvn clean deploy -Dmaven.test.skip=true "
            }
        }

    }
   post {
        success {
            emailext body: "The pipeline has completed successfully",
                attachLog: true,
                subject: "Jenkins pipeline completed successfully",
                to: "wafa.may@esprit.tn"
        }
        failure {
            emailext body: "The pipeline has failed",
                attachLog: true,
                subject: "Jenkins pipeline failed",
                to: "wafa.may@esprit.tn"
        }
    }

}
