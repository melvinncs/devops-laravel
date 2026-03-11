node {
 checkout scm

 stage("Build"){
  docker.image('composer:2').inside('-u root') {
   sh 'composer install'
  }
 }

 stage("Testing"){
  docker.image('ubuntu').inside('-u root') {
   sh 'echo "Ini adalah test"'
  }
 }

 stage("Deploy"){
  docker.image('agung3wi/alpine-rsync:1.1').inside('-u root') {
   sshagent(['ssh-pwd']) {
    sh 'mkdir -p ~/.ssh'
    sh 'ssh-keyscan -H "$PROD_HOST" > ~/.ssh/known_hosts'
    sh 'rsync -rav --delete ./ melvinncs@$PROD_HOST:/home/melvinncs/prod.kelasdevops.xyz/'
   }
  }
 }
}