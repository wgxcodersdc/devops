# Women Who Code DC - Cloud & DevOps - Winter 24 Kubernetes Workshop - Minikube
In this workshop we'll cover the basics of running a Kubernetes cluster, by setting up a virtual environment on your computer. Instructions will be provided for Windows and MacOS. These instructions are valid as of February 2024
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
8. Open a command prompt, and type docker version and hit enter
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
5. Open a terminal, and type docker version and hit enter
    * If Docker was installed correctly you will get info back about the installation

## Install Minikube

