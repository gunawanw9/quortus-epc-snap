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

To check your system is configured properly:
```shell
quortus-epc-lool.check-sys
```
Upon installation, the `ran` daemon is launched and creates a config file under
`/var/snap/quortus-epc-lool/current`.

Provision your license with the `rancli` tool:
```shell
quortus-epc-lool.rancli
```

Check the service is running or its output with:
```shell
sudo journalctl -u snap.quortus-epc-lool.ran
sudo systemctl status snap.quortus-epc-lool.ran
```

Restart the service with:
```shell
sudo systemctl restart snap.quortus-epc-lool.ran
```

