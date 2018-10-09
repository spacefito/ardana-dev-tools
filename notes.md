QUICK GUIDE:
============
Configure bash environment:
---------------------------
Add to ~/.bashrc (replace "ardanausername" with what you use).
 ```
export ARDANA_DEVELOPER=True
export ARDANA_VAGRANT_VERSION=1.8.7
export ARDANAUSER=ardanausername
export ARDANA_SITE=provo
eval "$(~/clm/ardana-dev-tools/bin/ardana-env)"
```

Install git:
-------------
```
sudo zypper install git-core
```
Install OSC:
------------
```
sudo zypper install osc
```
and connect to osc for the first time to configure credentials and certificates:
```
ardana@clm:~> osc ls

the apiurl 'https://api.suse.de' does not exist in the config file. Please enter
your credentials for this apiurl.

Username: someusername
Password:  ****
*** certificate verify failed at depth 3
Subject:  /C=DE/ST=Franconia/L=Nuremberg/O=SUSE Linux Products GmbH/OU=OPS Services/CN=SUSE Trust Root/emailAddress=rd-adm@suse.de
Issuer:   /C=DE/ST=Franconia/L=Nuremberg/O=SUSE Linux Products GmbH/OU=OPS Services/CN=SUSE Trust Root/emailAddress=rd-adm@suse.de
Valid:  Dec  6 00:00:00 2011 GMT - Dec  5 23:59:59 2041 GMT
Fingerprint(MD5):   65450722D4AA0FE988A8B70E10360D80
Fingerprint(SHA1):  D1311A7E8C2A04DD81C923F3410F2D752F0B7681
Reason: self signed certificate in certificate chain

A certificate in the chain failed verification

Would you like to
0 - quit (default)
1 - continue anyways
2 - trust the server certificate permanently
9 - review the server certificate

Enter choice [0129]: 2
Devel:AAC
... and a few thoushand lines more.
```


Install qemu-kvm:
-----------------
```
sudo zypper install qemu-kvm
```

Install libvirtd:
-----------------
```
sudo zypper install libvirt
systemctl status libvirtd
systemctl start libvirtd
usermod -aG libvirt ardanausername

```
Add user to kvm group:
---------------------
```
sudo usermod -aG kvm ardanausername
```

Clone repos:
------------
```
mkdir clm
cd clm
git clone https://github.com/spacefito/ardana-dev-tools.git
git clone https://github.com/spacefito/ardana-input-model.git
```

Set up runtime environment to assure correct ansible version is used:
---------------------------------------------------------------------
```
source ~/.bashrc
```
or 
```
eval "$(~/clm/ardana-dev-tools/bin/ardana-env)"
```

Setup/initialize development environment: 
-----------------------------------------
```
~/clm/ardana-dev-tools/bin/dev-env-setup
```

Checkout the branch you want to test:
-------------------------------------
```
cd ~/clm/ardana-input-model
git checkout stable/pike
cd ~/clm/ardana-dev-tools
git checkout stable/pike
```

Deploy a minimal system: 
------------------------
```
cd ~/clm/ardana-dev-tools/bin
./astack.sh  --c8 dac-min
```
