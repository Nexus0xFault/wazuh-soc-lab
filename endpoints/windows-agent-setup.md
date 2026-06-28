
# Windows Agent Setup for Wazuh

## Objective
Connect a Windows machine to the Wazuh server for log collection and security monitoring.

## Requirements
- Windows 10/11 (Pro)
- The Wazuh server is already running
- Internet access to download the agent

## Step 1: Download the Wazuh Agent

1. Open a browser on your Windows machine
2. Go to the official Wazuh website: https://documentation.wazuh.com/current/installation-guide/wazuh-agent/wazuh-agent-package-windows.html
3. On this page, look for the link to Windows Installer.
4. Download the Windows installer:
- Version: **4.14.5-1** (or the latest stable version)
- File: `wazuh-agent-4.14.5-1.msi`

## Step 2: Installing the Agent

1. Run the downloaded `.msi` file (as an administrator)
2. Tick the box next to `I accept the terms of the licence agreement` and click `Install`.
3. Tick the box next to `Run Agent configuration interface` and click `Finish`.

### Configuring the Server Connection

1. In the configuration window, you will see the `Wazuh Manager IP` field.
2. Enter the IP address of your Wazuh server: **If Wazuh is installed on the same machine:** specify `127.0.0.1`
3. After entering the IP click the `Manage` button in the upper-left corner of the window.
4. Select `Start` from the dropdown menu.
5. Click the `Refresh` button - an `Authentication key` should be automatically generated.
6. After the key appears, click `Save` to apply the configuration.

## Step 3: Checking the agent status

### Via the Windows interface

1. Open **Windows Services**:
- Press `Win + R`
- Type: `services.msc`
- Locate: **Wazuh Agent**

2. Check the status:
- ✅ Status: **Running**
- ✅ Startup type: **Automatic**

**Once you have completed all the steps listed above, you will be able to log in to the Wazuh control panel and check which devices are connected.**
