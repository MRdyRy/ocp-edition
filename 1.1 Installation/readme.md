## To Install Openshift on your computer, follow this step :
#### 1. Login or create a Red Hat account
Visit <a href="https://console.redhat.com">Red Hat</a> and sign in or create an account.
#### 2. go to Openshift Installation url
  https://console.redhat.com/openshift/create/local
#### 3. Select the "Local" tab on the right side.
#### 4. Choose your operating system
(In this guide, I’ll use Linux as an example.)
<img src="https://github.com/MRdyRy/ocp-edition/blob/main/1.1%20Installation/assets/prep.png" alt="download"/>
#### 5. Download the CRC (CodeReady Containers) archive
wait until the download is complete.
#### 6. Extract the downloaded file 
run this command :
```bash
tar xvf crc-linux-amd64.tar.xz
```
#### 7. Add the extracted folder to your system PATH 
```bash
export PATH=$PATH:[path]/crc-linux-2.49.0-amd64
```
#### 8. Verify the installation by running:
```bash
crc version
```
You should see an output similar to: :
<img src="https://github.com/MRdyRy/ocp-edition/blob/main/1.1%20Installation/assets/crc_ver.png" alt="crc version"/>
#### 9. Install required virtualization dependencies:
```bash
sudo apt install -y qemu-kvm libvirt-daemon libvirt-daemon-system
sudo addgroup libvirtd
sudo adduser $(whoami) libvirtd
sudo usermod -a -G libvirtd $(whoami)
newgrp libvirtd
sudo apt install network-manager
```
#### 10. Set up CRC (CodeReady Containers):
```bash
crc setup
```
<img src="https://github.com/MRdyRy/ocp-edition/blob/main/1.1%20Installation/assets/crc_set.png" alt="setup" />

#### 11. The installation process will begin. This may take 15–20 minutes until the cluster is fully ready.
#### 12. Verify the installation by running:
```bash
crc status
```
Or check the output:
<img src="https://github.com/MRdyRy/ocp-edition/blob/main/1.1%20Installation/assets/crc_ver.png" alt="crc version"/>
