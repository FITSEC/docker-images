# Docker setup for Intel Macbook: 

## 1. Download docker desktop here  
* https://runnable.com/docker/install-docker-on-macos  
* Click on the hyperlink Download Docker, to automatically download the file

<p align="center">
  <img src="https://github.com/FITSEC/docker_images/blob/main/cse1001_vnc/images/mac_intel.png" />
</p>


* Once docker is downloaded, double click the .dmg file in the downloads  

<p align="center">
  <img src="https://github.com/FITSEC/docker_images/blob/main/cse1001_vnc/images/dockermac1.png" />
</p>

* Drag the docker application into the Applications folder

<p align="center">
  <img src="https://github.com/FITSEC/docker_images/blob/main/cse1001_vnc/images/dockermac2.png" />
</p>

* Go to applications open docker  

<p align="center">
  <img src="https://github.com/FITSEC/docker_images/blob/main/cse1001_vnc/images/dockermac3.png" />
</p>

* Click on the docker icon

<p align="center">
  <img src="https://github.com/FITSEC/docker_images/blob/main/cse1001_vnc/images/dockermac4.png" />
</p>

* Click Open

<p align="center">
  <img src="https://github.com/FITSEC/docker_images/blob/main/cse1001_vnc/images/dockermac5.png" />
</p>

* Click Next

<p align="center">
  <img src="https://github.com/FITSEC/docker_images/blob/main/cse1001_vnc/images/dockermac6.png" />
</p>

* Click Okay

<p align="center">
  <img src="https://github.com/FITSEC/docker_images/blob/main/cse1001_vnc/images/dockermac7.png" />
</p>

* Enter your password when prompted
* Docker is starting

<p align="center">
  <img src="https://github.com/FITSEC/docker_images/blob/main/cse1001_vnc/images/dockermac8.png" />
</p>

* When you see this at the top, click the docker icon in the task bar

<p align="center">
  <img src="https://github.com/FITSEC/docker_images/blob/main/cse1001_vnc/images/dockermac9.png" />
</p>

* This will pop up, click Install Update

<p align="center">
  <img src="https://github.com/FITSEC/docker_images/blob/main/cse1001_vnc/images/dockermac10.png" />
</p>

* You will see the downloading screen and then Click Install and Relaunch

<p align="center">
  <img src="https://github.com/FITSEC/docker_images/blob/main/cse1001_vnc/images/dockermac11.png" />
</p>

<p align="center">
  <img src="https://github.com/FITSEC/docker_images/blob/main/cse1001_vnc/images/dockermac12.png" />
</p>

* Click Ok then enter your password

<p align="center">
  <img src="https://github.com/FITSEC/docker_images/blob/main/cse1001_vnc/images/dockermac13.png" />
</p>

* Check the box to accept the terms, then hit the Accept button

<p align="center">
  <img src="https://github.com/FITSEC/docker_images/blob/main/cse1001_vnc/images/dockermac14.png" />
</p>

## 2. Create a folder/directory for the class
* There are two ways to do this. The first will be more familiar, but the second is good to know, and you will have to learn it eventually

### A. Use Finder to create the file/directory  
* Click on the finder icon on the task bar

<p align="center">
  <img src="https://github.com/FITSEC/docker_images/blob/main/cse1001_vnc/images/finder1.png" />
</p>

* Navigate to the Documents tab by clicking on it in the left of the window

<p align="center">
  <img src="https://github.com/FITSEC/docker_images/blob/main/cse1001_vnc/images/finder2.png" />
</p>

* Right click in the main area and select New Folder  
* Rename it to cse1001 for the class

<p align="center">
  <img src="https://github.com/FITSEC/docker_images/blob/main/cse1001_vnc/images/finder3.png" />
</p>

* Right click on the folder and select "New Terminal at Folder"

<p align="center">
  <img src="https://github.com/FITSEC/docker_images/blob/main/cse1001_vnc/images/finder4.png" />
</p>

* A new terminal will pop open and you should paste the docker run command into it, change "changeme" to a password of your choosing, navigate using the arrow keys as the mouse does not work to select a place in the terminal, and hit enter

<p align="center">
  <img src="https://github.com/FITSEC/docker_images/blob/main/cse1001_vnc/images/macterm8.jpeg" />
</p>

```
docker run --detach --publish 6080:80 --volume "${PWD}":/home/cse1001/workspace:rw --env VNC_PASSWORD=changeme --env RESOLUTION=1400x825 --name cse1001_vnc tjoconnor/cse1001_vnc:latest
```

* Open a browser of your choice (I suggest Firefox) paste one of the following (they mean the same thing): http://127.0.0.1:6080/  or  http://localhost:6080


### B. Alternatively you could navigate in the terminal to create the directory/folder
* Hit Command + Space to open up the search

<p align="center">
  <img src="https://github.com/FITSEC/docker_images/blob/main/cse1001_vnc/images/macterm1.jpeg" />
</p>

* Type in the word "terminal"

<p align="center">
  <img src="https://github.com/FITSEC/docker_images/blob/main/cse1001_vnc/images/macterm2.jpeg" />
</p>

* A new terminal will pop open

<p align="center">
  <img src="https://github.com/FITSEC/docker_images/blob/main/cse1001_vnc/images/macterm4.png" />
</p>

* Type in the term "ls" this lists the contents of your current folder/directory, in theory it should open up in your "home" folder

<p align="center">
  <img src="https://github.com/FITSEC/docker_images/blob/main/cse1001_vnc/images/macterm4.png" />
</p>

* Now type in the term "mkdir cse1001", mkdir means make directory (or folder) and cse1001 is the name of the folder you're creating. Repeat "ls" to see that it is now in your home folder.

<p align="center">
  <img src="https://github.com/FITSEC/docker_images/blob/main/cse1001_vnc/images/macterm5.png" />
</p>

<p align="center">
  <img src="https://github.com/FITSEC/docker_images/blob/main/cse1001_vnc/images/macterm6.png" />
</p>

* Next type in "cd cse1001", cd means change directory (or folder), this will place you inside the folder you just created.

<p align="center">
  <img src="https://github.com/FITSEC/docker_images/blob/main/cse1001_vnc/images/macterm7.png" />
</p>

* You should paste the docker run command into the terminal, then change "changeme" to a password of your choosing and hit enter

<p align="center">
  <img src="https://github.com/FITSEC/docker_images/blob/main/cse1001_vnc/images/macterm8.jpeg" />
</p>

```
docker run --detach --publish 6080:80 --volume "${PWD}":/home/cse1001/workspace:rw --env VNC_PASSWORD=changeme --env RESOLUTION=1400x825 --name cse1001_vnc tjoconnor/cse1001_vnc:latest
```

* Open a browser of your choice (I suggest Firefox) paste one of the following (they mean the same thing): http://127.0.0.1:6080/  or  http://localhost:6080

## 3. Stopping and starting the container
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
