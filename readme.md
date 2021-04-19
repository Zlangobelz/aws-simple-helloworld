1. Build php container from dockerfile

**docker build -t php-ash -f ./docker/php/Dockerfile .**

2. Create a container from tagged image

**docker run -d --name php -p 9000:9000 php-ash**

3. Build container from dockerfile

**docker build -t nginx-ash -f ./docker/nginx/Dockerfile .**

4. Create a container from tagged image

**docker run -d --name nginx -p 8000:80 --link php:php-ash nginx-ash**

5. Create tag for docker image (nginx is an example for the next batch of commands)
**docker tag nginx-ash:latest 618342723525.dkr.ecr.us-west-2.amazonaws.com/ash-nginx**
   
6. Authorize into aws ecr console in docker
**docker login -u admin https://618342723525.signin.aws.amazon.com/console**

7. Get auth token and login with that token into ECR
**aws ecr get-login-password --region us-west-2 | docker login --username AWS --password-stdin 618342723525.dkr.ecr.us-west-2.amazonaws.com**
   
8. Push into image repository
**docker push 618342723525.dkr.ecr.us-west-2.amazonaws.com/ash-nginx:latest**
   
9. Pull images from ECR

**docker pull 618342723525.dkr.ecr.us-west-2.amazonaws.com/ash-nginx**

10. Create a container (command 4, but use repository from ecr)