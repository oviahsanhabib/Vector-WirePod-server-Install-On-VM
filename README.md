# Vector WirePod server Install On VM
This will provide step-by-step guidance for installing the WirePod server hosting on a Linux virtual machine running Ubuntu Server.


Ubuntu 20.04.6 LTS (Focal Fossa)


cd ~
git clone https://github.com/fforchino/wire-pod --depth=1


cd ~/wire-pod
sudo STT=vosk ./setup.sh


sudo ./chipper/start.sh



Starting webserver at port 8080 (http://localhost:8080)
Starting jdocs pinger ticker
Starting SDK app
Starting server at port 80 for connCheck
Configuration page: http://10.0.0.3:8080


sudo ~/wire-pod/setup.sh daemon-enable
sudo systemctl start wire-pod




sudo apt-get update
sudo apt-get install -y python3 python3-pip python3-tk python3-pil.imagetk build-essential libssl-dev libffi-dev freeglut3
pip3 install --upgrade setuptools


cd ~
git clone https://github.com/cyb3rdog/vector-python-sdk --depth=1




pip3 install cyb3r_vector_sdk

pip3 install "cyb3r_vector_sdk[3dviewer]"

pip uninstall protobuf
pip install protobuf==3.20.0

python3 -c "import anki_vector as _; print(_.__path__)"


python3 -m anki_vector.configure_pod


