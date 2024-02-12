# Women Who Code DC - Cloud & DevOps - Winter 24 Kubernetes Workshop - Minikube
In this workshop we'll cover the basics of running a Kubernetes cluster, by setting up a virtual environment on your computer. Instructions will be provided for Windows and MacOS. These instructions are valid as of February 2024.
Needed tools to have installed for this workshop
* [Docker](https://docker.com)
* [Minikube](https://minikube.sigs.k8s.io/)
* [Kubectl](https://kubernetes.io/docs/reference/kubectl/)
    * Kubectl is installed with Docker Desktop and doesn't need to be separately installed for this workshop
## Install Docker
### Windows
[System Requirements can be viewed here.](https://docs.docker.com/desktop/install/windows-install/#system-requirements)
[Full Instructions from Docker](https://docs.docker.com/desktop/install/windows-install/)

1. [Download the installer](https://desktop.docker.com/win/main/amd64/Docker%20Desktop%20Installer.exe?)
2. Run the Installer
3. When prompted, ensure the Use WSL 2 instead of Hyper-V option on the Configuration page is selected or not depending on your choice of backend.
    * If your system only supports one of the two options, you will not be able to select which backend to use.
4. Follow the instructions on the installation wizard to authorize the installer and proceed with the install.
5. When the installation is successful, select Close to complete the installation process.
6. Start the Docker Desktop from your Programs menu
7. Accept the license agreement.
8. Open a [powershell](https://learn.microsoft.com/en-us/powershell/scripting/install/installing-powershell-on-windows?view=powershell-7.4#installing-the-msi-package) window, and type `docker version` and hit enter
    * If Docker was installed correctly you will get info back about the installation

### MacOS
[System Requirements can be viewed here.](https://docs.docker.com/desktop/install/mac-install/#system-requirements)
[Full Instructions from Docker](https://docs.docker.com/desktop/install/mac-install/)

1. Download the installer
    * [M1 or newer Macs with Apple Silicon](https://desktop.docker.com/mac/main/arm64/Docker.dmg?)
    * [Intel Macs](https://desktop.docker.com/mac/main/amd64/Docker.dmg?)
2. Double-click the Docker.dmg file that was downloaded, and drag the Docker app to the Applications folder.
3. Run Docker Desktop from the Applications folder or Spotlight Search menu
4. Accept the license agreement
5. Open a terminal, and type `docker version` and hit enter
    * If Docker was installed correctly you will get info back about the installation

## Install Minikube

### Windows
[System Requirements can be viewed here.](https://minikube.sigs.k8s.io/docs/start/#what-youll-need)
[Full Instructions from Minikube](https://minikube.sigs.k8s.io/docs/start/)

1. [Download the installer](https://storage.googleapis.com/minikube/releases/latest/minikube-installer.exe)
2. Run the Installer
3. Open a Powershell window as Admin
    * Right-click on Powershell and choose Run As Administrator
4. Add the minikube.exe to your Environment's PATH via the Powershell Window, by copying and pasting the following commands. Hit Enter after each one.
    * `$oldPath = [Environment]::GetEnvironmentVariable('Path', [EnvironmentVariableTarget]::Machine)`
    * `if ($oldPath.Split(';') -inotcontains 'C:\minikube'){
          [Environment]::SetEnvironmentVariable('Path', $('{0};C:\minikube' -f $oldPath), [EnvironmentVariableTarget]::Machine)
       }`
5. Validate it has been added to the PATH by typing `minikube version`
    * If Minikube was installed correctly you will get info back about the installation
6. Close all powershell windows, and open a new winodw not as admin

### MacOS
[System Requirements can be viewed here.](https://minikube.sigs.k8s.io/docs/start/#what-youll-need)
[Full Instructions from Minikube](https://minikube.sigs.k8s.io/docs/start/)

1. Download the installer
    1. M1 or newer Macs with Apple Silicon
        1. Open a terminal and install by copying and pasting the following commands. Hit Enter after each one.
        2. `curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-darwin-arm64`
        3. `sudo install minikube-darwin-arm64 /usr/local/bin/minikube`
    2. [Intel Macs](https://desktop.docker.com/mac/main/amd64/Docker.dmg?)
        1. Open a terminal and install by copying and pasting the following commands. Hit Enter after each one.
        2. `curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-darwin-amd64`
        3. `sudo install minikube-darwin-arm64 /usr/local/bin/minikube`
2. Validate it has been added to the PATH by typing `minikube version`
    * If Minikube was installed correctly you will get info back about the installation

## Starting A Cluster
* From a Powershell or Terminal window, type 
    * `minikube start --kubernetes-version=1.29.1`
* We'll now wait for a number of tools to validate and download, and the cluster to start
* When it's finished and ready to use it will say `* Done! kubectl is now configured to use "minikube" cluster and "default" namespace by default`
* We can validate that kubectl is configured, by typing `kubectl --context=minikube describe namespace default`

## Cleanup
To save resources as Docker and Minikube can use quite a lot make sure to stop and exit the apps after you're done testing them!
### Minikube
* Run `minikube stop` in your Terminal or Powershell window
### Docker
* Windows
    * From the taskbar, right click and choose Stop
* Mac
    * From the File Menu, choose Quit