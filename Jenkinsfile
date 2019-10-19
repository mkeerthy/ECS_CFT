pipeline {
  agent any
  environment {
	 		AWS_ACCESS_KEY_ID = credentials('AWS_ACCESS_KEY_ID')
			AWS_SECRET_ACCESS_KEY = credentials('AWS_SECRET_ACCESS_KEY')
	  		AWS_REGION = "us-east-1"
			Stack_name = "ECSHelloWorld"	 
	 }
  parameters {
	  string(name: 'DesiredCapacity', defaultValue: "1", description: 'Number of desired EC2 instances') 
	  string(name: 'EnvironmentName', defaultValue: "ECS HelloWorld", description: 'ECS ClusterName') 
	  string(name: 'InstanceType', defaultValue: "t2.micro", description: 'Instance Type') 
	  string(name: 'KeyName', defaultValue: "mad")
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
	    sh "echo ${params.region}"	
		script{ datas = readYaml (file: 'create_ecs.yml') ${DesiredCapacity}. ${EnvironmentName}. ${InstanceType}. ${KeyName} }
	    sleep 30
            sh 'echo "Build step completed"'            
        }
      }
  }
}      
