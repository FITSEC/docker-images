If you need help with the installation of docker click [here](https://github.com/FITSEC/docker_images/tree/main/cse1001_vnc/docker_help).
Keep in mind that the instructions are tailored for the CSE1001 course, but the steps will be the same. 

Pull/run commands:

These commands include the bind/mount of a folder from the docker to your host computer. You can remove '-v' and the file path following it if you don't want to do that, and you can add -rm after run if you'd like the container to remove itself after every time you use it.

Windows/Linux/OSX: 
```
docker run --cap-add=SYS_PTRACE --cap-add=SYS_ADMIN --cap-add=audit_control --security-opt seccomp=unconfined --privileged --platform linux/amd64  -ti --name=cyber-ops tjoconnor/cyber-ops:latest
```
