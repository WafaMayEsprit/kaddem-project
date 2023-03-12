pipeline {

    agent any
    tools{
       maven 'Maven_Home' 
    }
    stages {
        stage ('GIT') {
            steps {
               echo "Getting Project from Git";
                git branch: "master",
                    url: "https://github.com/WafaMayEsprit/kaddem-project.git";
            }
        }

          stage("Build") {
            steps { 
                sh "mvn test"
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
