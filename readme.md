Pwd: /home/ec2-user/k3s/docker
mkdir certs
cd certs
 
### generate selfcert keypair with public & private key: keycloak.key and keycloak.crt
openssl req -newkey rsa:2048 -nodes   -keyout keycloak.key  -x509 -days 365 -out keycloak.crt   -subj "/CN=IP_PUBLIC"   -addext "subjectAltName=IP:IP_PUBLIC,DNS:localhost"
 
### edit docker-compose under docker folder "/home/ec2-user/k3s/docker" with params cert point to above certs:
### code docker-compose.yaml


### start container
docker-compose up -d
 
### access via https / http:
https://IP_PUB:8443/admin/master/console/
http://IP_PUB:8090/realms/master/
