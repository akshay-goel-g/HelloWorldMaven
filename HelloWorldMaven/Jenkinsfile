pipeline { 
    agent any 
    stages {
        stage('Build') { 
            steps {
                withMaven(maven : 'mvn'){
                        sh "mvn clean compile"
                }
            }
        }
        stage('Test'){
            steps {
                withMaven(maven : 'mvn'){
                        sh "mvn test"
                }

            }
        }
        stage('Publish') {
            steps {
                sh "pwd"
               //withMaven(maven : 'mvn'){
                 //       sh "mvn deploy"
                //}
                azureFunctionAppPublish  azureCredentialsId: 'c9c8631b-efcb-4367-9170-c89b3b95bc4b',
                             appName: 'Azurefunction',
                             filePath: '**/*.json,**/*.jar,bin/*,HttpTrigger-Java/*',
                             resourceGroup: 'myResourceGroup',
                             sourceDirectory: 'target/'
                                 
           
            }
        }
    }
}
