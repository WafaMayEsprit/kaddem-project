pipeline {

    agent any
    tools{
       maven 'MAVEN_HOME'
       jdk 'JAVA_HOME'
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
                sh "mvn -version"
                bat "mvn clean package -DskipTests"
            }
        }

    }

    post {
        always {
            cleanWs()
        }
    }

}