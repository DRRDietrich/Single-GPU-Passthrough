# Single-GPU-Passthrough
Fedora Linux AMD GPU

## Setup
Mainboard: ASUS TUF X470-PLUS GAMING
CPU: AMD Ryzen 5 2600X
RAM: 2x 8 GB DDR4 3000 MHz
GPU (Primary): AMD Radeon RX 580 8GB
GPU (only for CUDA): NVIDIA GeForce GTX 1060 6GB
OS: Fedora 33

### VM
see Windows.xml

### Scripts
mkdir /etc/libvirt/hooks
cd /etc/libvirt/hooks
vim qemu
chmod +x qemu

#### qemu
#!/bin/bash
if [[ $1 == "__VMNAME__"]]; then
  if [[ $2 == "prepare" ]]; then
    systemctl stop gdm.service;
  fi
  if [[ $2 == "release" ]]; then
    systemctl start gdm.service;
  fi
fi

### Troubleshooting
#!/bin/bash
systemctl isolate graphical.target

or

#!/bin/bash
systemctl reboot

