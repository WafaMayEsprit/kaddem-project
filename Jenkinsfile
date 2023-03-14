pipeline {

    agent any
    tools{
       maven 'Maven_Home'  
      
    }
    stages {
        stage ('GIT') {
            steps {
               echo "Getting Project from Git sss";
                git branch: "sonar",
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
                sh "mvn sonar:sonar   \
                -Dsonar.projectKey=test   \
                -Dsonar.host.url=https://8f4f-197-238-157-125.eu.ngrok.io   \ 
                -Dsonar.login=510a19ee7e890ad0df36314eb377c49b631898d5 \
                -Dsonar.login=admin -Dsonar.login=dali"
               
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
