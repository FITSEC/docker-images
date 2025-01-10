# Cyber-Ops Docker Container Installation

The reason for using Docker containers for FITSEC activities is to give members a somewhat disposable and secure environment to play CTFs.

Most issues with the cyber-ops container that cause it to be inoperable or unusable can be resolved by removing the `cyber-ops` container and recreating it with one of the `docker run` commands below.

## Install Docker on your system:
- Linux: `Dependent on your distribution. I would not recommend installing Docker-GUI.`
- Mac: Use the official Docker installation guide [here](https://docs.docker.com/desktop/install/mac-install/).
- Windows: Use the official Docker installation guide [here](https://docs.docker.com/desktop/install/windows-install/).
- Open system terminal (PowerShell not CMD shell for you Windows weirdos).
- Run "`docker version`" to test docker installation


## Pull image:
- When time permits run "`docker pull tjoconnor/cyber-ops:latest`". This may take a while depending on the network speed.
- Double check that the image was installed by running "`docker images`".
- You should see something like this:
```
REPOSITORY            TAG          IMAGE ID       CREATED        SIZE
tjoconnor/cyber-ops   latest       3a7a1c1a9d19   9 days ago     25GB
```


## Run container:

### Mount local folder into Docker Container
- This is useful to move files in and out of the container using your host OS's file explorer.

#### Windows

```powershell
docker run -v "%USERPROFILE%\Desktop\cyber-ops:/root/workspace" --cap-add=SYS_PTRACE --cap-add=SYS_ADMIN --cap-add=audit_control --security-opt seccomp=unconfined --privileged --platform linux/amd64  -ti --name=cyber-ops tjoconnor/cyber-ops:latest
```

#### Mac
```bash
docker run -v "~/Desktop/cyber-ops:/root/workspace" --cap-add=SYS_PTRACE --cap-add=SYS_ADMIN --cap-add=audit_control --security-opt seccomp=unconfined --privileged --platform linux/amd64  -ti --name=cyber-ops tjoconnor/cyber-ops:latest
```

#### Linux
```bash
docker run -v "~/Desktop/cyber-ops:/root/workspace" --cap-add=SYS_PTRACE --cap-add=SYS_ADMIN --cap-add=audit_control --security-opt seccomp=unconfined --privileged --platform linux/amd64  -ti --name=cyber-ops tjoconnor/cyber-ops:latest
```


### Don't mount local folder into Docker Container 
- Run this command to create and run the container.
```bash
docker run --cap-add=SYS_PTRACE --cap-add=SYS_ADMIN --cap-add=audit_control --security-opt seccomp=unconfined --privileged --platform linux/amd64  -ti --name=cyber-ops tjoconnor/cyber-ops:latest
```

## Optional

### Viewing GUI apps via X11 server
If you want to be able to see GUI apps, you must install an Xserver.

- Windows: install [VcXsrv](https://vcxsrv.com/) and run the Xlaunch shortcut when you want to use GUI apps from the Docker container.
- Mac: Follow this [guide](https://www.cyberciti.biz/faq/apple-osx-mountain-lion-mavericks-install-xquartz-server/) up to step 2. This is untested because the person writing this does not own a mac 😎.
- Linux: Have yet to test solutions.

## Notes
- You can start and run the container with the commands "`docker start cyber-ops && docker exec cyber-ops /bin/zsh`" or "`docker start -ai cyber-ops`". Mileage may vary depending on your environment. If you have docker desktop then you don't have to think about it.
- Run "`docker ps`" if you want to see if the container is running.
- Run "`docker stop cyber-ops`" to stop the container if at all necessary.