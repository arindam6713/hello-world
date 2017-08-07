pipeline {
  agent any
  stages {
    stage('Check-Server-Available') {
      steps {
        sh '''#!/bin/bash
HOSTS="172.31.29.39"

COUNT=4

for myHost in $HOSTS
do
  count=$(ping -c $COUNT $myHost | grep 'received' | awk -F',' '{ print $2 }' | awk '{ print $1 }')
  if [ $count -eq 4 ]; then
{

    # 100% failed 
    echo "Host : $myHost is Available: ping passed at $(date)"
}

  else 
{
    # 100% failed 
    echo "Host : $myHost is Not Available: ping Failed at $(date)"
}
  fi
done'''
        waitUntil()
      }
    }
  }
}