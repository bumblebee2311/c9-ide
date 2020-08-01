# c9-ide
Local Hosting c9 IDE inside docker desktop
1. Download and install [Docker Desktop](www.docker.com/products/docker-desktop) for Windows 64-bit (recommended)/ MacOS/ Linux 
    NOTE: Windows users need to enable virtualization support from BIOS

### Method 1 (Easier Way!)
```zsh
docker run --name cloud9 -p 3000:3000 -d bumblebee2311/c9-ide:latest
```
It would automatically download docker image and automatically start a container named as <b>cloud9</b> on host port 3000
On IP address 0.0.0.0:3000 (accessible via browser)

To stop an already running container <b>docker ps </b> (Container NAMES <b>Cloud9</b>)
```zsh
docker stop cloud9
```

To re-work in the working environment 
```zsh
docker start cloud9
```

For more docker documentation ref <b>https://docs.docker.com</b>
or use  <b>docker --help </b> which returns a list of valid commands on docker desktop CLI

To get help on docker command
```zsh
docker COMMAND --help
```

### Method 1 (Tough Way!)
2. Downlod this GitHub repository [c9-ide](github.com/bumblebee2311/c9-ide)
3. Un-zip the compresses file downloaded (c9-ide.zip) in yr Downloads folder.
4. Start Docker Desktop in yr OS
5. Start yr respective cmd line (PowerShell for Windows Users & Terminal for Linux/ MacOS terminal)
6. Navigate to yr respective Downloads folder. 
    PowerShell/ Terminal : cd ~/Downloads 
7. Validate proper installation of Docker Desktop 
```zsh 
docker version
```
It would return information somewhat similar as shown in image below
<img src="https://storage.googleapis.com/static.configserverfirewall.com/images/docker/docker-version-command.png">

7. Using Docker Desktop to build image using <b>Dockerfile</b>
```zsh
docker build Cloud9
```
8. It would take time to build complete docker img using Dockerfile and init.sh and would require internet connection for additional pkg downloads.
9. After complete image buildup, chk for its presence
```zsh
docker images
```
It would return attributes like REPOSITORY, TAG, IMAGE ID, CREATED, and SIZE and list all the images present probably ubuntu and c9-IDE.
Since, ubuntu is used as base img to build Cloud9

10. Create container from the installed img using the command
```zsh
docker run --name Cloud9:latest -p 3000:3000 -d c9:latest
```
11. This would create a container and would return container ID, to see all active and inactive containers present with attributes like 
CONTAINER ID, IMAGE, COMMAND, CREATED, STATUS, PORTS, NAMES execute cmd
```zsh
docker ps -a
```
To see all active containers
```zsh
docker ps
```
12. Now, the Web IDE is ready for use, copy the CONTAINER ID from <b>docker ps -a</b> and replace <b>CONTAINER ID</b> with it
```zsh
docker start CONTAINER ID
```
On, successful start it would return the same container ID

13. Go to your favourite browser in your computer and type 0.0.0.0:3000

##### And Bingo!
It would redirect you to Cloud9 interface, providing similar experience as of AWS Cloud9.
##### NOTE:
  The terminal login is already as root user.
  So, to install additional pkgs one doesn't need to use sudo every time, just apt-get install pkg_name 

##### Advantages 
1. Provides complete isolated file system as of host computer.
2. Best for testing and running web application on host computer.
3. Doesn't acquire size in GB as compared to Virtual Machines.
4. Easy to setup and use.
5. Provides the utility to setup quich 

##### To, remove the container when you feel like as if you messes up something 
Copy CONTAINER ID from <b>docker ps -a</b>
Stop the container <b>docker stop CONTAINER ID</b>
And execute 
```zsh
docker rm CONTAINER ID
```
And it's done!

Since, the original image is already present (<b>docker images</b>) one can recreate the container from step 10.

To, delete docker image one needs to delete it's corresponding child containers first
After that copy IMAGE ID from <b>docker images</b> and execute 
```zsh
docker rmi IMAGE ID
```

More updates on the way soon ...
<b>Happy Coding :D </b>
