pipeline {
  agent any
  stages {
    stage('Start-Job') {
      steps {
        sh '''#!/bin/bash
HOSTS="172.31.29.39"

COUNT=4

for myHost in $HOSTS
do
  count=$(ping -c $COUNT $myHost | grep 'received' | awk -F',' '{ print $2 }' | awk '{ print $1 }')
  if [ $count -eq 0 ]; then
    # 100% failed 
    echo "Host : $myHost is down (ping failed) at $(date)"
  fi
done'''
        waitUntil()
      }
    }
  }
}