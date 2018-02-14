# My Own Library for Docker Containers

## Hello

Hello World, This is `hello` repository for image building example.

```
$ make
gcc -static -Wall hello.c -o hello
$ 
$ docker build -t hello .
Sending build context to Docker daemon  813.1kB
Step 1/3 : FROM scratch
 --->
Step 2/3 : COPY hello /
 ---> 73bb9ea905cb
Step 3/3 : CMD ["/hello"]
 ---> Running in f6f0088c2335
Removing intermediate container f6f0088c2335
 ---> 50eaed409e2a
Successfully built 50eaed409e2a
Successfully tagged hello:latest
$
$ docker run hello
hello from docker container
$
```

That's all!

