pipeline {
  agent any
  stages {
    stage('Check-Server-Available') {
      steps {
        sh '''
#!/bin/bash

HOST="172.31.29.39"
COUNT=4


for myHost in $HOSTS
do
  count=`$(ping -c $COUNT $myHost | grep 'received' | awk -F',' '{ print $2 }' | awk '{ print $1 }')`

  if [[ $count -eq $COUNT ]] ; then
  { 
    echo "Host : $myHost is down (ping failed) at $(date)"
  }
  else
  {
    echo "Host : $myHost is Available (ping Passed) at $(date)"
  }
fi
done

'''
      }
    }
  }
}