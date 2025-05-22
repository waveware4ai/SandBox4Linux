# SandBoxForNVIDIA

1. This SandBox is used to use Python/nVidia GPUs on various Linux distributions.
2. This SandBox is built on Ubuntu22 and tested on CentOS7, CentOS8, Ubuntu20.x, Ubuntu22.x, Ubuntu24.x.

Installation
------------
This SandBox can be unpacked and run in any path.
```
tar xvfz sandbox-0.1.x86_64-linux.b20241018.tar.gz
```
Then, Perform install using the command below.
```
sudo ./sandbox.install.sh ./sandbox-0.1.x86_64-linux
```
Entry into the sandbox is performed through a pre-created chroot script.
```
sudo ./sandbox.chroot.sh ./sandbox-0.1.x86_64-linux
```
Unnstallation
------------
You can uninstall it using the command below and just delete it.
```
sudo ./sandbox.install.sh ./sandbox-0.1.x86_64-linux
sudo rm -rf ./sandbox-0.1.x86_64-linux
```
Using SandBox
------------
Waiting to write ....
