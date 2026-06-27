

# Install Wazuh on Docker in Windows

## We need:

- Windows 10/11 (Pro)
- WSL 2 enabled and installed
- Virtualization enabled in BIOS/UEFI
- CPU: At least 4 cores
- Memory: At least 8 GB of RAM for the Docker host
- Disk space: At least 50 GB storage for Docker images and data volumes

## Step 0: Install Git

If Git is not installed, download and install it from: https://git-scm.com/download/win

### Verify installation:

```powershell
git --version
```

## Step 1: Install Docker Desktop on Windows

### Download Docker Desktop

Visit the official download page: https://docs.docker.com/desktop/setup/install/windows-install/

### Run the installer:

- Double-click the downloaded Docker Desktop Installer.exe
- Follow the default installation settings
- Important: Ensure the option "Use WSL 2 instead of Hyper-V" is checked during installation
    
Restart your computer when prompted

### Launch Docker Desktop:

- After restart, Docker Desktop will start automatically
- Accept the license agreement
- Wait for the Docker engine to start (you'll see the whale icon in the system tray)
    
### Verify installation

Open PowerShell or Command Prompt and run:
```powershell
docker --version
docker-compose --version
```

## Step 2: Clone Wazuh from GitHub and Generate Certificates

### Clone the Official Wazuh Docker Repository

Create a directory and clone the repository
    
```powershell
mkdir C:\wazuh-docker
cd C:\wazuh-docker
git clone https://github.com/wazuh/wazuh-docker.git -b v4.14.5
cd wazuh-docker\single-node
```

### Generate TLS Certificates

Wazuh requires certificates for secure communication between its components. Generate them using the built-in generator:

Using PowerShell:

```powershell
docker-compose -f generate-indexer-certs.yml run --rm generator
```

The generated certificates will be stored in the `config/wazuh_indexer_ssl_certs` directory.

### Pull Required Docker Images

Pre-pull images for faster deployment:

```powershell
docker-compose pull
```

## Step 3: Start the Wazuh Stack

Launch the containers:

```powershell
docker-compose up -d
```

### Wait for initialization (5-10 minutes depending on your system)

The command will:

- Pull Docker images if not already pulled
- Create and start three main containers:

Wazuh Indexer (OpenSearch) - port 9200

Wazuh Server (Manager) - ports 1514, 1515, 55000

Wazuh Dashboard - port 443

### Check container status

```powershell
docker-compose ps
```

All containers should show "Up" status:
```text
NAME                      IMAGE                         STATUS
wazuh-dashboard           wazuh/wazuh-dashboard:4.14.5  Up 2 minutes
wazuh-indexer             wazuh/wazuh-indexer:4.14.5    Up 2 minutes (healthy)
wazuh-manager             wazuh/wazuh-manager:4.14.5    Up 2 minutes (healthy)
```

## Step 4: Access the Wazuh Dashboard

Open your browser and navigate to:

```text
https://localhost
```

### Security warning

Click "Advanced" → "Proceed to localhost" (self-signed certificate)

### Login credentials:

- Username: admin
- Password: SecretPassword

### You're in! 🎉

You should now see the Wazuh dashboard with:

- Security events overview
- Agent status
- Alerts and vulnerabilities
