pipeline {
agent {
label 'Build-server'
}

stages {

stage ('Checkout') 
{
steps
    {
    
        checkout scm
        
    }
    
}
stage ('Build') 
{
    steps
    {
       sh "/home/ubuntu/workspace/pipelineproject/spring-microservices ; mvn clean install " 
    }
}

   
stage ('dockerimageBuild')
    {
    steps
    {
        sh "/home/ubuntu/workspace/pipelineproject/spring-microservices ; sudo docker build -t spring-microservices . " 
    }
}
     stage ('dockerimagepush ') 
{
    steps
    {
       sh "/home/ubuntu/workspace/ pipelineproject/spring-microservices ; sudo  docker login -urajender17 -pRajender@340 "
        sh "/home/ubuntu/workspace/ pipelineproject/spring-microservices ; sudo docker tag spring-microservices rajender17/account-service "
        sh "/home/ubuntu/workspace/ pipelineproject/spring-microservices ; sudo docker push rajender17/spring-microservices  "
        
        
    }
}
    
    
stage ('k8sdeployment') 
    {
        steps {
            node (' Ansible-server') {
             sh " sudo ansible-playbook /root/k8s.yaml"
   
    }
}
}
}
    
    
}
