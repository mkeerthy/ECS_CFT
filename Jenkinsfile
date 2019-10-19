pipeline {
  agent any
  parameters {
        string(DesiredCapacity: 1, EnvironmentName: 'ECS HelloWorld', InstanceType: 't2.micro', KeyName: 'mad')
  }
  
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
      
