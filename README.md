# Packer for proxmox template

## Description

*Preseeding* is used to answers questions asked during the installation process.

## Start / Setup

Add your RSA public key, to the file `cloud.cfg` it will be used to connect to the VM:

```bash
# We use '#' because there is '/' that can be interpreted
$ sed -i "s#ssh-rsa AAAA.*#$(cat ~/.ssh/id_rsa.pub)#" cloud.cfg
```

To start the script use:

```
$ packer build -var-file variables.json debian11.json
```

## Limitations

Cloud-init doesn't support lvm resize by default. You can change `cloud.cfg` to make it work or not use lvm at all.

## Links
- https://github.com/romantomjak/packer-proxmox-template
- https://www.packer.io/docs/builders/proxmox/iso