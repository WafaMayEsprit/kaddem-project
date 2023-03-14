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
                sh 'mvn org.sonarsource.scanner.maven:sonar-maven-plugin:3.9.1.2184:sonar'
                sh "mvn sonar:sonar  \
                -Dsonar.host.url=http://127.0.0.1:9092  \
                -Dsonar.projectKey=69c5dbbc056985269e7abec2d307dcadd8fce3f9 "
               
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
