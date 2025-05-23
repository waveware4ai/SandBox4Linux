# SandBox4Linux

This SandBox provides an isolated environment for using PotablePython/nVidiaGPUs on various Linux distributions.  
This is built on Ubuntu22 and tested on CentOS7, CentOS8, Ubuntu20.x, Ubuntu22.x, Ubuntu24.x.  

Additionally, you can create the most convenient environment possible when using it with zimport/PortablePython at the link below.  
https://github.com/waveware4ai/zimport  
https://github.com/waveware4ai/PortablePython  

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
```bash
sudo ./sandbox.chroot.sh ./sandbox-0.1.x86_64-linux

[INF] enter chroot ...[sandbox-0.1.x86_64-linux]
Welcome sandbox-0.1 ...
# This package was built based on debootstrap, ubuntu 22.04.
# also, tested on centos7.1,7.3,7.8,7.9 and ubuntu 20.x, 21.x, 22.x
# additionally, portable python version 3.9, 3.10, 3.11, 3.12 is included.
#
# by 14mhz@hanmail.net, zookim@waveware.co.kr@20241015
===========================================
0. importance !!!
   - if you haven't run the 'sandbox.install.sh' script, run it first (only once).
   - it is needed to communicate with the kernel and makes system commands available.
   - eg, lsmod, lspci, nvidia-smi ...
1. when logging into the sandbox for the first time,
   - run : useradd -m -d /home/newuser -s /bin/bash newuser
   - run : passwd newuser
   - you can also create a different username.
2. configuration for sshd
   - specify the port number for initial sshd service. default 22022
   - run : if you need, run 'vi /etc/ssh/sshd_config'
3. start service sshd
   - start service only once when starting the sandbox.
   - run : /usr/sbin/sshd -D &
4. connect with ssh client
   - connect with the created user account eg, newuser
5. using python
   - you can decompress /home/*.tar.gz anywhere and just use it!!!.
   - for install pip, run command './python python.pip'
6. stop & remove sandbox
   - exit chroot using the ^d/exit key.
   - get pid of sshd using cmd : 'sudo lsof -ti :22022'
   - terminate sshd using cmd : 'kill -9 [PID]'
   - remove link&mount to kernel using cmd : 'sandbox.uninstall.sh'
   - delete sandbox, anyway ...
===========================================
```
SandBox is isolated from the host and has a complete Ubuntu22 environment, even if it is a different Linux distribution.  
In other words, useradd is possible internally, and a separate sshd daemon can also be run.  
In conclusion, you can create a portable environment that is completely isolated from the host system, 
and if you use Python and nVidia GPU, it can provide the best testing/service environment.  
※ Portable Python can be downloaded by referring to the link below.  
https://github.com/waveware4ai/PortablePython  

nVidia Driver Pass-Through
------------
SandBox has nVidia Driver pass-through feature, so if you have installed nvidia driver on the host, you can access GPU inside SandBox.
```bash
root@Test:/# whoami
root
root@Test:/# nvidia-smi
Fri May 23 19:54:45 2025
+-----------------------------------------------------------------------------------------+
| NVIDIA-SMI 550.144.03             Driver Version: 550.144.03     CUDA Version: 12.4     |
|-----------------------------------------+------------------------+----------------------+
| GPU  Name                 Persistence-M | Bus-Id          Disp.A | Volatile Uncorr. ECC |
| Fan  Temp   Perf          Pwr:Usage/Cap |           Memory-Usage | GPU-Util  Compute M. |
|                                         |                        |               MIG M. |
|=========================================+========================+======================|
|   0  NVIDIA GeForce GTX 1060 3GB    Off |   00000000:01:00.0 Off |                  N/A |
|  0%   36C    P8              7W /  200W |      68MiB /   3072MiB |      0%      Default |
|                                         |                        |                  N/A |
+-----------------------------------------+------------------------+----------------------+

+-----------------------------------------------------------------------------------------+
| Processes:                                                                              |
|  GPU   GI   CI        PID   Type   Process name                              GPU Memory |
|        ID   ID                                                               Usage      |
|=========================================================================================|
|    0   N/A  N/A       893      G   /usr/lib/xorg/Xorg                             56MiB |
|    0   N/A  N/A      1043      G   /usr/bin/gnome-shell                            8MiB |
+-----------------------------------------------------------------------------------------+
root@Test:/#
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
