# WirePod Server Hosting Setup Guide

This guide provides step-by-step instructions for setting up WirePod server hosting on a Linux virtual machine running Ubuntu Server (version 20.04.6 LTS - Focal Fossa).

## Prerequisites

Before starting the setup process, ensure you have the following:

- Linux virtual machine running Ubuntu Server 20.04.6 LTS (Focal Fossa)
- Internet connection
- sudo access privileges

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
Conclusion
You have successfully set up WirePod server hosting on your Ubuntu Server. You can now utilize the functionalities provided by the WirePod server and interact with Vector robots using the Python SDK.
For more information and advanced usage, refer to the project's documentation on GitHub.
Note: Make sure to replace any placeholder values such as IP addresses or URLs with your actual server information.
