pipeline{
    agent any
    tools{
    	maven 'local_maven'
    }
    stages{
        stage ('Build'){
            steps{
                sh 'mvn clean package'
            }
            post{
                success{
                    echo "Archiveing the Artifacts"
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }
        stage ('Deploy to tomcat server'){
            steps{
		deploy adapters: [tomcat9(credentialsId: 'tomcat-cred', path: '', url: '')], contextPath: null, war: '**/*.war'
	    }
	}
    }
}
