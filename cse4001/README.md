# os161 docker setup

If you need help with the installation of docker click [here](https://github.com/FITSEC/docker_images/tree/main/cse4001_vnc/docker_help).
Keep in mind that the instructions are tailored for the CSE4001 VNC, but the steps will be the same up until the command to run the container. 

Pull/run commands:  
These commands include the bind/mount of a folder from the docker to your host computer. You can remove '-v' and the file path following it if you don't want to do that, and you can add -rm after run if you'd like the container to remove itself after every time you use it.

Windows: 
```
docker run -v "$(PWD):/root/workspace" -ti --name cse4001 tjoconnor/cse4001:latest
```

Linux/Intel Mac:
```
docker run -v $(PWD):/root/workspace -ti --name cse4001 tjoconnor/cse4001:latest
```

M1/M2 Mac:
```
docker run -v $(PWD):/root/workspace -ti --platform linux/amd64 --name cse4001 tjoconnor/cse4001:latest
```
