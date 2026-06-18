pipeline{
  agent any
  tools{
    maven 'Maven'
  }
  environment{
    LANG='eng_US.UTF-8'
    LC_ALL='eng_US.UTF-8'
  }
  stages{
    stage('Checkout'){
      steps{
        git branch:'main',url:'https://github.com/Brijesh-ue/AnsibleEx.git'
      }
    }
    stage('Build'){
      steps{
        sh 'mvn clean package'
      }
    }
    stage('Test'){
      steps{
        sh 'mvn test'
      }
    }
    stage('Archive'){
      steps{
        archiveArtifacts artifacts 'target/*.war' , fingerprint:true
      }
    }
    stage('Deploy'){
      steps{
        sh 'ansible-playbook ansbile/playbook.yml -i ansible/hosts.ini'
      }
    }
  }
}
