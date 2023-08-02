# Docker setup for windows:

*** Please note that even if you are using docker via the command line/powershell, in order for the docker daemon to be running docker desktop has to be open.

## 1. Download docker desktop  
* https://www.docker.com/products/docker-desktop/  
* Click Windows and it should automatically start downloading

<p align="center">
  <img src="https://github.com/kourtnee/cse1001-novnc/blob/master/images/windows1.png" />
</p>

* Once it's downloaded click on the file icon in the task bar

<p align="center">
  <img src="https://github.com/FITSEC/docker_images/blob/main/cse1001_vnc/images/file1.png" />
</p>

* Click on downloads in the menu on the left

<p align="center">
  <img src="https://github.com/FITSEC/docker_images/blob/main/cse1001_vnc/images/file2.png" />
</p>

* Double click on the Docker Desktop Installer, when prompted to give docker permission accept

<p align="center">
  <img src="https://github.com/FITSEC/docker_images/blob/main/cse1001_vnc/images/windows1.png" />
</p>

* Click Ok

<p align="center">
  <img src="https://github.com/FITSEC/docker_images/blob/main/cse1001_vnc/images/windows2.png" />
</p>

* Docker will start to download

<p align="center">
  <img src="https://github.com/FITSEC/docker_images/blob/main/cse1001_vnc/images/windows3.png" />
</p>

* Once it's done you can click Close

<p align="center">
  <img src="https://github.com/FITSEC/docker_images/blob/main/cse1001_vnc/images/windows4.png" />
</p>

* Go to the desktop and double click the docker icon

<p align="center">
  <img src="https://github.com/FITSEC/docker_images/blob/main/cse1001_vnc/images/windows5.png" />
</p>

* Check the accept box, then click the Accept button

<p align="center">
  <img src="https://github.com/FITSEC/docker_images/blob/main/cse1001_vnc/images/windows6.png" />
</p>



## 2. Follow instructions for WSL (if prompted once docker installs)  
https://docs.microsoft.com/en-us/windows/wsl/install-manual

* Step 6: Install your Linux distro of choice -> shouldn’t be necessary unless you plan to use it outside the course



## 3. Create a folder/directory for the class
* There are two ways to do this. The first will be more familiar, but the second is good to know, and you will have to learn it eventually

### A. Use File Explorer to create the file/directory  
* Click on the finder icon on the task bar

<p align="center">
  <img src="https://github.com/FITSEC/docker_images/blob/main/cse1001_vnc/images/file1.png" />
</p>

* Navigate to the Documents tab by clicking on it in the left of the window

<p align="center">
  <img src="https://github.com/FITSEC/docker_images/blob/main/cse1001_vnc/images/file2.png" />
</p>

* Right click in the main area and select New Folder  
* Rename it to cse1001 for the class

<p align="center">
  <img src="https://github.com/FITSEC/docker_images/blob/main/cse1001_vnc/images/file3.png" />
</p>

<p align="center">
  <img src="https://github.com/FITSEC/docker_images/blob/main/cse1001_vnc/images/file4.png" />
</p>

* Double click on the name cse1001 to go into the folder, then hold shift and right click in the folder and select "Open PowerShell window here"

<p align="center">
  <img src="https://github.com/FITSEC/docker_images/blob/main/cse1001_vnc/images/file5.png" />
</p>

* A new terminal will pop open and you should paste the docker run command into it, change "changeme" to a password of your choosing, navigate using the arrow keys as the mouse does not work to select a place in the terminal, and hit enter

<p align="center">
  <img src="https://github.com/FITSEC/docker_images/blob/main/cse1001_vnc/images/file7.png" />
</p>

```
docker run -d -p 6080:80 -v "$(PWD):/home/cse1001/workspace:rw" -e "RESOLUTION=1440x900" -e "VNC_PASSWORD=changeme" --name "cse1001-run" "tjoconnor/cse1001_vnc:latest"
```

* Open a browser of your choice (I suggest Firefox) paste one of the following (they mean the same thing): http://127.0.0.1:6080/  or  http://localhost:6080


### B. Alternatively you could navigate in the terminal to create the directory/folder
* Type PowerShell into the search bar on the bottom left (for school computers you might be able to use cygwin if you prefer)

<p align="center">
  <img src="https://github.com/FITSEC/docker_images/blob/main/cse1001_vnc/images/power1_1.png" />
</p>

* A new terminal will pop open
* Type in the term "ls" this lists the contents of your current folder/directory, in theory it should open up in your "home" folder

<p align="center">
  <img src="https://github.com/FITSEC/docker_images/blob/main/cse1001_vnc/images/power1.png" />
</p>

* Now type in the term "mkdir cse1001", mkdir means make directory (or folder) and cse1001 is the name of the folder you're creating. Repeat "ls" to see that it is now in your home folder.

<p align="center">
  <img src="https://github.com/FITSEC/docker_images/blob/main/cse1001_vnc/images/power2.png" />
</p>

* Next type in "cd cse1001", cd means change directory (or folder), this will place you inside the folder you just created.

<p align="center">
  <img src="https://github.com/FITSEC/docker_images/blob/main/cse1001_vnc/images/power3.png" />
</p>

* You should paste the docker run command into the terminal, then change "changeme" to a password of your choosing and hit enter

<p align="center">
  <img src="https://github.com/FITSEC/docker_images/blob/main/cse1001_vnc/images/power5.png" />
</p>

```
docker run -d -p 6080:80 -v "$(PWD):/home/cse1001/workspace:rw" -e "RESOLUTION=1440x900" -e "VNC_PASSWORD=changeme" --name "cse1001-run" "tjoconnor/cse1001_vnc:latest"
```

* Open a browser of your choice (I suggest Firefox) paste one of the following (they mean the same thing): http://127.0.0.1:6080/  or  http://localhost:6080


## 4. Stopping and starting the container
* The GUI (Graphical User Interface) for docker allows starting and stopping to be very simple.

* To stop hit the square icon between the refresh and trash icons

<p align="center">
  <img src="https://github.com/FITSEC/docker_images/blob/main/cse1001_vnc/images/gui1.png" />
</p>

* To start hit the play (triangle) icon

<p align="center">
  <img src="https://github.com/FITSEC/docker_images/blob/main/cse1001_vnc/images/gui2.png" />
</p>

* For information on navigating docker via the terminal click [here](https://github.com/FITSEC/docker_images/blob/main/cse1001_vnc/docker_help/Navigating_Containers.md)
