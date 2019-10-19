pipeline {
  agent any
  environment {
	 		AWS_ACCESS_KEY_ID = credentials('AWS_ACCESS_KEY_ID')
			AWS_SECRET_ACCESS_KEY = credentials('AWS_SECRET_ACCESS_KEY')
	  		AWS_REGION = "us-east-1"
	 }
  parameters {
	  string(name: 'DesiredCapacity', defaultValue: "1", description: 'Number of desired EC2 instances') 
	  string(name: 'EnvironmentName', defaultValue: "ECS HelloWorld", description: 'ECS ClusterName') 
	  string(name: 'InstanceType', defaultValue: "t2.micro", description: 'Instance Type') 
	  string(name: 'KeyName', defaultValue: "mad")
  } 
  stage('Build') {
        steps {
            sh 'echo "Build step started"'
	    aws cloudformation create-stack --stack-name ECSHelloWorld --template-url https://mad-ecstest.s3.amazonaws.com/ecs-updated.yml --parameters ParameterKey=DesiredCapacity,ParameterValue=1,ParameterKey=EnvironmentName,ParameterValue=ECS HelloWorld,ParameterKey=InstanceType,ParameterValue=t2.micro,ParameterKey=KeyName,ParameterValue=mad	
	    sleep 30
            sh 'echo "Build step completed"'            
        }
      }
  }
}      
