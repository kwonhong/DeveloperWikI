#### Installing Virtual Box
* You need to call this script with **sudo**

##### Mac Version:  Installing Virtual Box
``` shell
#!/bin/bash

# Declaring Versions & Directory to install
VIRTUALBOX_CACHE_DIR=$(mktemp -d /VirutalBoxCache)
VIRTUALBOX_VERSION="5.0.2"
VIRTUALBOX_BUILD_NUMBER="102096"
VIRTUALBOX_FULL_VERSION="${VIRTUALBOX_VERSION}-${VIRTUALBOX_BUILD_NUMBER}"
VIRTUALBOX_INSTALLER_FILENAME="VirtualBox-${VIRTUALBOX_FULL_VERSION}-OSX.dmg"

# Getting virtualBox dmg file from the website
if [[ ! -f ${VIRTUALBOX_CACHE_DIR}/${VIRTUALBOX_INSTALLER_FILENAME} ]]; then
    echo "Preparing cache dir..."
    mkdir -p ${VIRTUALBOX_CACHE_DIR}
    echo "Downloading installer disk image..."
    wget -c http://download.virtualbox.org/virtualbox/${VIRTUALBOX_VERSION}/${VIRTUALBOX_INSTALLER_FILENAME} -O ${VIRTUALBOX_CACHE_DIR}/${VIRTUALBOX_INSTALLER_FILENAME}
fi

# Mounting the disk image
echo  "Mounting installer disk image..."
hdiutil mount ${VIRTUALBOX_CACHE_DIR}/${VIRTUALBOX_INSTALLER_FILENAME}

# Installing the virtualBox
echo  "Running installer..."
pushd /
sudo /usr/sbin/installer -pkg /Volumes/VirtualBox/VirtualBox.pkg -target /
popd

# UnMounting the disk image
echo "Unmounting installer disk image..."
hdiutil eject /Volumes/VirtualBox
```

##### Linux Version:  Installing Virtual Box
``` shell
if [[ -z $(grep "deb http://download.virtualbox.org/virtualbox/debian vivid contrib" /etc/apt/sources.list) ]]; then
    echo_verbose "Adding VirtualBox APT key..."
    wget -qO- https://www.virtualbox.org/download/oracle_vbox.asc | sudo apt-key add -
    echo_verbose "Adding VirtualBox APT repository..."
    echo "deb http://download.virtualbox.org/virtualbox/debian vivid contrib" | sudo tee -a /etc/apt/sources.list
    echo_verbose "Running apt-get update..."
    sudo apt-get -qq update
fi
echo_verbose "Running apt-get install virtualbox-5.0..."
sudo apt-get -y install virtualbox-5.0 dkms

if [[ -z $(VBoxManage list extpacks | grep "Oracle VM VirtualBox Extension Pack") ]]; then

VIRTUALBOX_VERSION=$(VBoxManage -v)
VIRTUALBOX_VERSION_MAJOR=$(echo ${VIRTUALBOX_VERSION} | cut -d 'r' -f 1)
VIRTUALBOX_VERSION_MINOR=$(echo ${VIRTUALBOX_VERSION} | cut -d 'r' -f 2)
VIRTUALBOX_EXTPACK_INSTALLER_FILENAME="Oracle_VM_VirtualBox_Extension_Pack-${VIRTUALBOX_VERSION_MAJOR}-${VIRTUALBOX_VERSION_MINOR}.vbox-extpack"
VIRTUALBOX_CACHE_DIR=${CACHE_DIR}/virtualbox
if [[ ! -f ${VIRTUALBOX_CACHE_DIR}/${VIRTUALBOX_EXTPACK_INSTALLER_FILENAME} ]]; then
    echo_verbose "Preparing cache dir..."
    mkdir -p ${VIRTUALBOX_CACHE_DIR}
    echo_verbose "Downloading extension pack..."
    wget -c http://download.virtualbox.org/virtualbox/${VIRTUALBOX_VERSION_MAJOR}/${VIRTUALBOX_EXTPACK_INSTALLER_FILENAME} -O ${VIRTUALBOX_CACHE_DIR}/${VIRTUALBOX_EXTPACK_INSTALLER_FILENAME}
fi
echo_verbose "Installing extension pack..."
VBoxManage extpack install ${VIRTUALBOX_CACHE_DIR}/${VIRTUALBOX_EXTPACK_INSTALLER_FILENAME}
```
