# deploy-a-reverse-proxy-server

first the application we used to deploy the reverse proxy for is the beetroot api, found here : https://github.com/skandix/Beetroot.git
we will deploy different services and configure it to work as reverse proxy in containers using docker

1- build the api:
- the docker file structured as a multistages docker file to reduce the image size

2- Apache as a proxy server:
- the docker compose runs 2 containers one for the api and the other for the httpd service
- the confg file that makes apache act as reverse proxy is mounted to the container

2- nginx as a proxy server:
- the docker compose runs 2 containers one for the api and the other for the nginx
- the confg file that makes nginx act as reverse proxy is mounted to the container

2- Traefik as a proxy server:
- the docker compose runs 2 containers one for the api and the other for the traefik
- the configuration that makes traefik act as reverse proxy is provided in the docker compose file 
