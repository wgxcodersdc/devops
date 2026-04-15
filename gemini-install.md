# Install Google Gemini CLI

## Notes
Gemini CLI is cross-platform, using an Node.js backend, so we will be checking and installed Node.js (20.x+) and then installing Gemini CLI. You will likely need Administrator permissions on your computer for this. Resource requirements for install are lightweight, and will generally work on any computer newer than 2018.

## Installing Node.JS

### MacOS Instructions
Install Node.js using Homebrew:
```bash
brew install node
```

If you don't have Homebrew installed, get it first at [brew.sh](https://brew.sh), or download the macOS installer directly from [nodejs.org/en/download](https://nodejs.org/en/download).

### Windows Instructions
Install Node.js using Chocolatey:
```bash
choco install nodejs
```

If you don't have Chocolatey installed, download the Windows Installer (.msi) directly from [nodejs.org/en/download](https://nodejs.org/en/download).

### Linux Debian/Ubuntu/.DEB Instructions
```bash
curl -fsSL https://deb.nodesource.com/setup_24.x | sudo -E bash -
sudo apt-get install -y nodejs
```

### Linux RHEL/RPM Instructions
```bash
curl -fsSL https://rpm.nodesource.com/setup_24.x | sudo bash -
sudo yum install nodejs
```

## Installing Gemini CLI

### MacOS Instructions
```bash
brew install gemini-cli
```

Or install via npm:
```bash
npm install -g @google/gemini-cli
```

### Windows Instructions
```bash
npm install -g @google/gemini-cli
```

### Linux Debian/Ubuntu/.DEB Instructions
```bash
npm install -g @google/gemini-cli
```

### Linux RHEL/RPM Instructions
```bash
npm install -g @google/gemini-cli
```

## Official Gemini and Node.JS Resource Links
[Gemini CLI Open Source Github Repo](https://github.com/google-gemini/gemini-cli)
[Gemini CLI Install Instructions Detailed](https://geminicli.com/docs/get-started/installation/)
[Node.js Download and Install Instructions](https://nodejs.org/en/download)
