  /*
  node {
   //sh "cd C://Program Files (x86)//Jenkins//workspace"
   sh "liquibase --changeLogFile=sample.changelog.sql --username=admin --password=oDnIIZHz9VCcDjfi9JOm --classpath=/mysql-connector-java-5.1.49/mysql-connector-java-5.1.49-bin.jar --url=jdbc:mysql://liquibasedev.c8n59c8tfijh.us-east-1.rds.amazonaws.com:3306/liquibasedev update"
}
*/
pipeline {
    options {
        ansiColor('xterm')
    }
    agent { label 'master' }
    stages {
        stage('Unit Testing')
                {
                    steps {
                        echo 'Testing'
                    }
                }
        stage('Liquibase') {
            steps {
                withCredentials([usernamePassword(credentialsId: "LIQUIBASE", usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {
                    sh 'echo $USERNAME $PASSWORD'
                    sh """
            liquibase --changeLogFile=sample.changelog.sql --username=$USERNAME --password=$PASSWORD --classpath=/opt/liquibase/mysql-connector-java-5.1.49-bin.jar --url=jdbc:mysql://liquibasedev.c8n59c8tfijh.us-east-1.rds.amazonaws.com:3306/liquibasedev update && \
            echo "\033[42m Liquibase Execution Suceess \033[0m" 
            """
                }
            }
        }
            stage('Compare schema with previous stage')
                    {
                        steps {
                            echo 'comparing schema'
                        }
                    }
        }
    }
