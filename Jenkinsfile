pipeline {
  agent none
  stages {
    stage('Check-Server-Available') {
      steps {
        sh '''Server="ADAMS-MYSQL"
Service_Name="mysqld"

ansible-playbook -v /etc/ansible/playbook/service_action_start.yml --extra-vars "HOST=$Server SERVICE=$Service_Name " -e 'ansible_python_interpreter="/usr/bin/env python"'
'''
        build(job: 'Service Action', quietPeriod: 2)
      }
    }
  }
}