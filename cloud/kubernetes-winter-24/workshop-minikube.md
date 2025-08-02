# WGXC DC - Cloud & DevOps - Winter 24 Kubernetes Workshop - Minikube
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

## Launching A Dashboard
The Kubernetes open source project offers a free basic dashboard app, and the Minikube project offers a simplified install as part of it's features.
* From a Powershell or Terminal window, type
    * `minikube addons enable metrics-server`
        * This will give us detailed metrics and telemetry to help us understand the system
    * `minikube dashboard &`
        * This tells minikube to start the dashboard and continue running it in the background by the use of the POSIX & command. Without the & the command will not allow you to type additional commands.
* Now you can go to the URL provided by minikube, if it didn't open a browser. An example output for me was:
    * `Opening http://127.0.0.1:65021/api/v1/namespaces/kubernetes-dashboard/services/http:kubernetes-dashboard:/proxy/ in your default browser...`
* From here you can explore what's available to this and all Kubernetes clusters using ver 1.29!

## Launching A Hello World application
Now that we have a cluster, a dashboard to visualize our system, it's time to launch our first app. For this we'll use kubectl to interact with the kubernetes api.
* From a Powershell or Terminal window, type
    * `kubectl create deployment hello-node --image=registry.k8s.io/e2e-test-images/agnhost:2.39 -- /agnhost netexec --http-port=8080`
        * This creates a simple node.js app
* You can now go back to your browser and see the deployment in the dashboard
* We can explore this deployment's configuration, see how much cpu, ram and pod count it's setup to currently use
* One thing we can't currently do is view the Hello Node app in our browser, let's fix that by creating a service and exposing it to localhost!
* From a Powershell or Terminal window, type
    * `kubectl expose deployment hello-node --type=LoadBalancer --port=8080`
        * This creates and exposes a LoadBalancer object for the hello-node deployment to attach to
    * `minikube service hello-node &`
        * This will tell minikube to create a service hello-node and make it accessible to your computer, and automatically open a browser window with the application.
* If you wanted to explore and see all services available you can run the following command
    * `minikube service list`

## Cleanup
To save resources as Docker and Minikube can use quite a lot make sure to stop and exit the apps after you're done testing them!
### Minikube
* Run `minikube stop` in your Terminal or Powershell window
### Docker
* Windows
    * From the taskbar, right click and choose Stop
* Mac
    * From the File Menu, choose Quit