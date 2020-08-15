docker pull jenkins/jenkins:lts
docker run -d -p 8080:8080 -p 50000:50000 -v jenkins_home:/var/jenkins_home jenkins/jenkins:lts
docker exec -it elated_tesla cat /var/jenkins_home/secrets/initialAdminPassword

docker run -it --rm \
  --name swarmpit-installer \
  --volume /var/run/docker.sock:/var/run/docker.sock \
  -e INTERACTIVE=0 \
  -e ADMIN_USERNAME=admin \
  -e ADMIN_PASSWORD=qwerty \
  swarmpit/install:edge
  
	
