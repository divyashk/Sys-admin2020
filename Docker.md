# Docker

## Question -1

The built image can be run by using the following command from anywhere, by anyone.

```bash  
$docker run divyashk/divyashk
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
* Then I created a Dockerfile 'inside' this cloned directory(important) to build the image.
  ```bash
  $touch Dockerfile
  ```
*  The file is written like this-
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

    # launching the application
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

## Question -2



