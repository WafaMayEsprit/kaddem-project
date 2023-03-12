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
                sh "mvn sonar:sonar \
                -Dsonar.projectKey=sonarname   \
                -Dsonar.host.url=http://localhost:9092/   \
                -Dsonar.login=69c5dbbc056985269e7abec2d307dcadd8fce3f9 \
                -Dsonar.login=admin -Dsonar.login=ESPRIT123"
            }
        }
        
        stage("Build") {
            steps {
                sh "mvn -version"
                sh "mvn clean package -DskipTests"
            }
        }

    }
 post {
        always {
            cleanWs()
        }
    }

}
