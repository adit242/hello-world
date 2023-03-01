pipeline{
    agent any
    tools{
        maven 'maven'
    }
    
    stages{
            stage("git code"){
                steps{
                    git credentialsId: 'git_credentials', url: 'https://github.com/ravdy/hello-world.git'
                }
            }
            stage("build code"){
                steps{
                    sh "mvn clean install"
                }
            }
            stage("deploying to tomcat")
            {
                steps{
                    deploy adapters: [tomcat9(credentialsId: 'tomcatCred', path: '', url: 'http://192.168.31.210')], contextPath: 'WebApp', war: '**/*.war'
                }
            }
        }
        
}
