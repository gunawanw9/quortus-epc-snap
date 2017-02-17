# Building

This snap should be built on an amd64 system with i386 enabled in APT as to
pull the 32-bits libstdc++; to do this run:
```shell
sudo dpkg --add-architecture i386
sudo apt update
```

To build:
```shell
sudo apt install snapcraft
snapcraft
```

# Installation

Install a locally built snap with:
```shell
sudo snap install --devmode *.snap
```

Or from a store:
```shell
sudo snap install --devmode --beta quortus-epc-lool
```

# Setup and operation

Check your system is configured properly:
```shell
quortus-epc-lool.check-sys
```

To achieve basic network setup (mainly forwarding and NAT) run the following
command and add it to your startup scripts:
```shell
sudo quortus-epc-lool.setup-networking
```

Upon installation, the `ran` daemon is launched. It creates a config file under
`/var/snap/quortus-epc-lool/current` which you may edit; restart the service to
pick up changes:
```shell
sudo vi /var/snap/quortus-epc-lool/current/ran.cfg
sudo systemctl restart snap.quortus-epc-lool.ran
```

Provision your license with the `rancli` tool:
```shell
quortus-epc-lool.rancli
```

Check the service is running or follow its output with:
```shell
sudo systemctl status snap.quortus-epc-lool.ran
sudo journalctl -u snap.quortus-epc-lool.ran -f
```

