pipeline
{
    agent any
    stages
    {
        stage('continuous downloading')
        {
            steps
            {
                git 'https://github.com/intelliqittrainings/maven.git'
            }
        }
        stage('continuous build')
        {
            steps
            {
                sh 'mvn package'
            }
        }
        stage('continuous deploy')
        {
            steps
            {
                deploy adapters: [tomcat9(credentialsId: '68b25502-765d-4595-abf6-f484185c866e', path: '', url: 'http://18.236.133.81:8080')], contextPath: 'test', war: '**/*.war'
            }
        }
        stage('continuous test')
        {
            steps
            {
                git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
                sh 'java -jar /var/lib/jenkins/workspace/declarative-pipeline1/testing.jar'
                
            }
        }
        stage('continuous delivery')
        {
            steps
            {
                deploy adapters: [tomcat9(credentialsId: '68b25502-765d-4595-abf6-f484185c866e', path: '', url: 'http://35.85.58.178:8080')], contextPath: 'prod', war: '**/*.war'
            }
        }
        
    }
}
