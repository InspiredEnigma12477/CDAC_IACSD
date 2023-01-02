# Docker Commands for NodeJS App

## Get to sudo Mode
- just because you can

```
sudo su
```
## Update the Linux Distro
### This is for the AWS Linux EC2
```
yum update 
```
### Install git to clone the repo
```
yum intsall git
```
### Install Docker 
```
yum install docker
```
### Check the status Docker Process
```
systemctl status docker
```
### Start the Docker Process
```
systemctl enable docker
systemctl start docker
```
### Clone the repo with simple NodeApp 
In this we have created a simple Express app that can take the user input of firstname and lastname and display the output

```
git clone https://github.com/InspiredEnigma12477/nodeapp.git
cd nodeapp
```
## Dockerfile
 > Note : Name the file as Dockerfile

```
FROM node:7
WORKDIR /app
COPY package.json /app
RUN npm install
COPY . /app
CMD node server.js
EXPOSE 6969
```
>Note : Possible errors 
> - you have created the file inside the <code> src</code>, it should be at root directory
> - given unwanted spaces
> - Dockerfile name is case-sensitive
> - node:7 not working use node:latest
> - look for silly mistakes like spelling, cases !! 😅
 



### Build the docker image using the Docker file from the repo
In this we use build alias to build the image and `-t` to give an alias or nametag to the image

```
docker build -t nodeapp .
```
### List the Available Docker Images
```
docker images
```

### Run the image
In this we run the images mentioned with the 
- external Port 8000
- internal port 6969
- -d for Run container in background and print container ID
- -p for Publishing a container's port(s) to the host

```
docker run -d -p 8000:6969 nodeapp
```
### Docker Process Status
```
docker ps
```
### Docker close the process 
```
docker kill hashcode
```
### Docker remove the image from the machine
```
docker rmi <name_image OR hashcode>  -f
```
