pipeline {
  agent any
  environment {
	 		AWS_ACCESS_KEY_ID = credentials('AWS_ACCESS_KEY_ID')
			AWS_SECRET_ACCESS_KEY = credentials('AWS_SECRET_ACCESS_KEY')
	 }
  parameters {
        string(Name: DesiredCapacity, defaultValue: '1', description: 'Number of desired EC2 instances')
        string(Name: EnvironmentName, defaultValue: 'ECS HelloWorld', description: 'ECS ClusterName')
        string(Name: InstanceType, defaultValue: 't2.micro', description: 'Instance Type')
        string(Name: KeyName, defaultValue: 'mad')
  }
  stages {
      stage('Test') {
            steps {
                sh 'echo "Fail!"; exit 1'
            }
      }
   stage('Build') {
        steps {
            sh 'echo "Build step started"'
            script{ datas = readYaml (file: 'create_ecs.yml') }
            sh 'echo "Build step completed"'            
        }
      }
  }
}      
