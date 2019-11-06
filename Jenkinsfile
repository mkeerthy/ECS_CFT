pipeline {
  agent any
  //environment {
  //	 		AWS_ACCESS_KEY_ID = credentials('AWS_ACCESS_KEY_ID')
  //			AWS_SECRET_ACCESS_KEY = credentials('AWS_SECRET_ACCESS_KEY')
  //	  		AWS_REGION = "us-east-1"
  //	 }
  // parameters {
  //	  string(name: 'DesiredCapacity', defaultValue: "1", description: 'Number of desired EC2 instances') 
  //	  string(name: 'EnvironmentName', defaultValue: "ECS HelloWorld", description: 'ECS ClusterName') 
  //	  string(name: 'InstanceType', defaultValue: "t2.micro", description: 'Instance Type') 
  //	  string(name: 'KeyName', defaultValue: "mad")
  // } 
  stages {
      stage('Build') {
          steps {
	      withAWS(credentials: 'AWS_JenkinsAccess', region: 'us-east-1') {
		    sh 'echo "Build step started"'
	    //aws cloudformation create-stack --stack-name ECSHelloWorld --template-url https://mad-ecstest.s3.amazonaws.com/ecs-updated.yml --parameters ${DesiredCapacity}. ${EnvironmentName}. ${InstanceType}. ${KeyName}	
	            def outputs = cfnUpdate(stack:'my-stack', file:'ecs-updated.yml', params:['DesiredCapacity'='1','EnvironmentName': 'ECS HelloWorld','InstanceType'= 't2.micro','KeyName'='mad'], keepParams:['Version'], timeoutInMinutes:10, tags:['TagName=Value'], notificationARNs:['arn:aws:sns:us-east-1:317246864222:GitrRepo_update:topic'], pollInterval:1000, onFailure:'DELETE')
	    //def outputs = cfnUpdate(stack:'my-stack', file:'template.yaml', params:['InstanceType': 't2.nano'], keepParams:['Version'], timeoutInMinutes:10, tags:['TagName=Value'], notificationARNs:['arn:aws:sns:us-east-1:993852309656:topic'], pollInterval:1000)
			//sleep 30
                    sh 'echo "Build step completed"'            
             }
         }
      }
   }      
}
