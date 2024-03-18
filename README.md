# WirePod Server Hosting Setup Guide

This guide provides step-by-step instructions for setting up WirePod server hosting on a Linux virtual machine running Ubuntu Server (version 20.04.6 LTS - Focal Fossa).

## Prerequisites

Before starting the setup process, ensure you have the following:

- [Linux virtual machine running Ubuntu Server 20.04.6 LTS (Focal Fossa)](https://releases.ubuntu.com/focal/ubuntu-20.04.6-live-server-amd64.iso)
- Internet connection
  
## Step 1: Download Ubuntu Server ISO
Go to the Ubuntu website's [download](https://releases.ubuntu.com/focal/ubuntu-20.04.6-live-server-amd64.iso) page.

Under "Ubuntu 20.04.6 LTS", click on the "Download" button for the "Server" version.

Choose a nearby location to download the ISO file.

## Step 2: Install Hyper-V
Open "Control Panel" on your Windows machine.

Click on "Programs" > "Programs and Features".

Click on "Turn Windows features on or off".

Check the box next to "Hyper-V" and click "OK".

Restart your computer if prompted.

## Step 3: Create a New Virtual Machine in Hyper-V
Open Hyper-V Manager.

Click on "Action" in the menu, then select "New" > "Virtual Machine".

In the "New Virtual Machine Wizard", click "Next".

Enter a name for your virtual machine and choose a location to store it, then click "Next".

Choose the generation for the virtual machine. For Ubuntu Server 20.04, choose "Generation 2" and click "Next".

Assign memory (RAM) to the virtual machine. A minimum of 4 GB is recommended for Ubuntu Server, but you can allocate more if needed. Click "Next".

Configure networking if necessary and click "Next".

Create a new virtual hard disk for the virtual machine. Specify the size (at least 30 GB is recommended), choose a location, and click "Next".

Choose the installation options. Select "Install an operating system from a bootable CD/DVD-ROM" and select "Image file (.iso)". Browse to the location where you downloaded the Ubuntu Server ISO file and click "Next".

Review the settings and click "Finish" to create the virtual machine.

## Step 4: Install Ubuntu Server on the Virtual Machine
Select the newly created virtual machine in Hyper-V Manager.

Right-click on the virtual machine and select "Settings" from the context menu. This will open the settings window for the virtual machine.

In the settings window, navigate to the "Security" section on the left-hand side.

Within the "Security" section, you should see an option for "Secure Boot." Uncheck or toggle the setting to disable Secure Boot.

![image](https://github.com/oviahsanhabib/Vector-WirePod-server-Install-On-VM/assets/104899177/13208dcf-f3c5-4334-a3c6-94d2037415ac)

After disabling Secure Boot, click "Apply" or "OK" to save the changes.

Start the Virtual Machine:

Once the settings are saved, close the settings window and start the virtual machine by right-clicking on it and selecting "Start."

Click on "Connect" in the Actions pane to open the Virtual Machine Connection window.

Start the virtual machine by clicking "Start" in the Virtual Machine Connection window.

Follow the on-screen instructions to install Ubuntu Server:

Choose your language.

Select "Install Ubuntu Server" and press Enter.

Follow the prompts to configure language, keyboard layout, network settings, etc.

When prompted, select "Guided - use entire disk and set up LVM" for partitioning.
Give server name as "escapepod"

Create a user account and password.

Complete the installation process.

## Step 5: Post-Installation Configuration
Once the installation is complete, remove the installation media (the ISO file) from the virtual machine.

Restart the virtual machine.

Log in with the credentials you created during the installation process.

Your Ubuntu Server 20.04.6 LTS virtual machine on Hyper-V is now set up and ready for use.

## Installation Steps

1. Clone the WirePod repository:

```bash
cd ~
git clone https://github.com/fforchino/wire-pod --depth=1
```
Navigate to the cloned directory and run the setup script:
```bash
cd ~/wire-pod
sudo STT=vosk ./setup.sh
```
Start the WirePod server:
```bash
sudo ./chipper/start.sh
```

Enable the WirePod daemon and start the service:
```bash
sudo ~/wire-pod/setup.sh daemon-enable
sudo systemctl start wire-pod
```
After compeleting these steps, you can follow [kercre123](https://github.com/kercre123/wire-pod/wiki/Installation) github page to pair your vector with your newly created wirepod server.

## Python SDK installation to run python script

Update the system packages and install required dependencies:
```bash
sudo apt-get update
sudo apt-get install -y python3 python3-pip python3-tk python3-pil.imagetk build-essential libssl-dev libffi-dev freeglut3
```
Clone the Vector Python SDK repository:
```bash
cd ~
git clone https://github.com/cyb3rdog/vector-python-sdk --depth=1
```
Install the Cyb3r Vector SDK and its dependencies:
```bash
pip3 install cyb3r_vector_sdk
```
```bash
pip3 install "cyb3r_vector_sdk[3dviewer]"
```
Update the Protobuf version:
```bash
pip uninstall protobuf
pip install protobuf==3.20.0
```
Check Vector SDK:
```bash
python3 -c "import anki_vector as _; print(_.find_data_files())"
```
```bash
python3 -m anki_vector.configure_pod
```
When prompted, enter your Vector's name.

Enter your Vector's IP address.

Enter your Vector's serial number.

Ensure that you have the correct information available to provide during the authorization process. This information is typically found on the packaging or documentation that came with your Vector robot.

Once you have entered the required information, the authorization process will proceed, and your Vector robot should be authorized to interact with your system.

## Conclusion

You have successfully set up WirePod server hosting on your Ubuntu Server. You can now utilize the functionalities provided by the WirePod server and interact with Vector robots using the Python SDK.
For more information and advanced usage, refer to the project's documentation on GitHub.

