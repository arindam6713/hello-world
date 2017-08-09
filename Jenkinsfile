pipeline {
  agent any
  stages {
    stage('Check-Server-Available') {
      steps {
        parallel(
          "Check-Server-Available": {
            sh '''
#!/bin/bash

HOSTS="172.31.29.39";
COUNT=4;

for myHost in $HOSTS
do
  count=$(ping -c $COUNT $myHost | grep 'received' | awk -F',' '{ print $2 }' | awk '{ print $1 }')

  if [[ $count -eq 0 ]] ; then
  { 
    echo "Host : $myHost is down (ping failed) at $(date)"
    exit 1;
  }
  else
  {
    echo "Host : $myHost is Available (ping Passed) at $(date)"
  }
fi
done

'''
            
          },
          "Check-DB-Process": {
            sh '''echo "Calling Ansible Playbook to check the status of mysqld process"

ansible-playbook /etc/ansible/playbook/check_sql.yml

if [[ $? -eq 0 ]]; then
{
echo "Mysqld process in Running"
}
else
{
echo "Mysqld process is not running"
exit 1;
}
fi
'''
            
          }
        )
      }
    }
    stage('Take-Action') {
      steps {
        sh '''echo " Taking action based on result of previous jobs"
'''
      }
    }
  }
}