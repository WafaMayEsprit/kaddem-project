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
                -Dsonar.login=69c5dbbc056985269e7abec2d307dcadd8fce3f9 \
                -Dsonar.host.url= http://192.168.43.42:9092/  "


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
        always {
            cleanWs()
        }
    }

}
