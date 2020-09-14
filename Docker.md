# Docker

>Remember, all the docker command require root privileges unless otherwise configured. The 'sudo' part of these commands is not included in my explanation but is very much required in a non-root account. 


## Question -1

The built image can be run by using the following command from anywhere, by anyone.

```bash  
$docker run divyashk/divyashk     # Since the run command looks for the image online if not found locally, therefore no need to pull the image first.
```
This gives the following output on being run.
```bash 
> baat-cheet@0.0.0 start /baatcheet
> node app.js

Listening 3000

# the logs will come here

```
>Be advised, if you want to view the application running in the container, use 'docker run' with appropriate flags to determine the right port.
> ```bash
> $docker run -it -p 3000:3000 divyashk/divyashk
> ```
> Now the site can be viewed in the browser using localhost at port 3000.


I achieved this result by proceding as follows.
* First I cloned the [baat-cheet](https://github.com/KamandPrompt/baat-cheet.git) app from github.
* Then I created a Dockerfile **inside** this cloned directory to build the image.
  ```bash
  $touch Dockerfile
  ```
*  The Dockerfile is written like this-
    ```Dockerfile
    #for creating a base image that runs nodejs
    FROM node:latest-slim 

    # setting the working dir for execs
    WORKDIR /baat-cheet

    # installing all the dependencies
    COPY package.json /baat-cheet
    RUN npm install 

    # adding all the file from the application to the image for creating the container later.
    COPY . /baat-cheet

    # launching the application in the container
    CMD ["npm", "start"]

    ```
  * Now I created an Image using this Dockerfile
    ```bash
    $docker build -t divyashk/divyashk .
    ```
  * This image I later pushed to my repository at hub.docker.com.
    ```bash
    $docker push divyashk/divyashk
    ```



## Question -3


* First, pulled the image.
  ```bash
  $docker pull httpd       #would default to httpd:latest
  ```
* This image now needs to be run with the '-v' flag that uses docker volumes to map Host-OS's files to the Container files. 
  ```bash
  $docker run -dit --name apache-container -p 8080:80 -v /home/dk/docker-vol:/usr/local/apache2/htdocs/ httpd  # would default to httpd:latest
  ```
* This would create a new directory named 'docker-vol' in /home/dk, but the read-write permissions would need to be changed to achieve the desired convenience.
  
  For changing the permissions-
  ```bash
  $sudo chmod 700 /home/dk/docker-vol/
  ```
Now, all the files in the container will be mapped to /home/dk/docker-vol and all the changes made here will be reflected in the container.