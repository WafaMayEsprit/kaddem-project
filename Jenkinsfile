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
                -Dsonar.host.url=https://e653-197-20-32-192.eu.ngrok.io/  "
                sh 'mvn org.sonarsource.scanner.maven:sonar-maven-plugin:3.9.1.2184:sonar'
               
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
