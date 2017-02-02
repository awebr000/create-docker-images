# Description
this repository is for you who first time use docker and don't know to build your first image.
as you can see, this repository is contain simple service but can work well.

### Step build Docker Images
1. Open 2 tab shell/terminal. Make sure your docker is running in first shell with command `dockerd`.
   if there's error `Permission Denied` you have to run it with command `sudo dockerd`.

2. Now in second shell. Make a new directory with your application inside it.
   (in this repo contain a localhost application made by Node.Js).

3. After that create a new file again inside your application directory named `Dockerfile`.
   (See Dockerfile inside this repo)

4. Build the Docker images with command:
```
$ docker build -t your/docker-image-name ./

//if you run sudo dockerd before, this command should looked like this

$ sudo docker build -t your/docker-image-name ./

Sending build context to Docker daemon  7.68 kB
Step 1/8 : FROM node:latest
latest: Pulling from library/node
5040bd298390: Pull complete
fce5728aad85: Pull complete
76610ec20bf5: Pull complete
52f3db4b5710: Pull complete
7e5867712a67: Pull complete
563b602246dd: Pull complete
b63b7336ef88: Pull complete
Digest: sha256:aa90bf69be3b6c29d7c877a2a12414ec908272eaa91422732b9270a3e19b3421
Status: Downloaded newer image for node:latest
 ---> b554dc4860d7
Step 2/8 : RUN mkdir -p /usr/src/app
 ---> Running in b1c1cb7e3774
 ---> 95bc1f9227ea
Removing intermediate container b1c1cb7e3774
Step 3/8 : WORKDIR /usr/src/app
 ---> a9b3046ecb21
Removing intermediate container 6282e4041346
Step 4/8 : COPY package.json /usr/src/app/
 ---> ac5c4f018d05
Removing intermediate container 00144f4d66dc
Step 5/8 : RUN npm install
 ---> Running in ebff082215ac

.....
..... < installation message >
.....

npm WARN expressjs-restful@1.0.0 No repository field.
npm info ok
 ---> d0270459b5c9
Removing intermediate container ebff082215ac
Step 6/8 : COPY . /usr/src/app
 ---> 6380ae399088
Removing intermediate container fdecaacbdd1d
Step 7/8 : EXPOSE 8080
 ---> Running in 9b126dc5ff31
 ---> bac6efa53f37
Removing intermediate container 9b126dc5ff31
Step 8/8 : CMD node index.js
 ---> Running in 9bd5ed9fb7e7
 ---> bf0167e88692
Removing intermediate container 9bd5ed9fb7e7
  Successfully built bf0167e88692
```

5. You can check your images with command `docker images` in your terminal


6. And try to run your service now with command:
```
$ docker run -p 49160:8080 -d your/docker-image-name
```

7. Test your service using port access with curl command
```
$ curl -i localhost:49160
```
8. And Done!
