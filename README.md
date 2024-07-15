# Raspberrypi5yoctoprojects
**Required packagaes setup:**
sudo apt-get update
sudo apt-get install gawk wget git-core diffstat unzip texinfo gcc-multilib \
    build-essential chrpath socat cpio python3 python3-pip python3-pexpect \
    xz-utils debianutils iputils-ping python3-git python3-jinja2 libegl1-mesa \
    libsdl1.2-dev pylint3 xterm

**Clone the Poky Repository:**
Clone the main Yocto Project repository, Poky.
git clone -b kirkstone git://git.yoctoproject.org/poky.git
cd poky

**Clone Additional Required Layers:**
Clone any additional layers that might be required for your build. 
git clone -b kirkstone git://git.openembedded.org/meta-openembedded

**Source the Environment Setup Script:**
Source the environment setup script to set up the build environment.
source oe-init-build-env

**Configure bblayers.conf:**
Edit conf/bblayers.conf to include the meta-raspberrypi and other required layers. Add the following lines to your bblayers.conf file:
BBLAYERS ?= " \
  ${TOPDIR}/../../poky/meta \
  ${TOPDIR}/../../poky/meta-poky \
  ${TOPDIR}/../../poky/meta-yocto-bsp \
  ${TOPDIR}/../meta-raspberrypi \
  ${TOPDIR}/../meta-openembedded/meta-oe \
  ${TOPDIR}/../meta-openembedded/meta-multimedia \
  ${TOPDIR}/../meta-openembedded/meta-networking \
  ${TOPDIR}/../meta-openembedded/meta-python \
"
**Configure local.conf:**
Edit conf/local.conf to set the machine to Raspberry Pi 5. Add or modify the following lines:
MACHINE ??= "raspberrypi5"

**Start the Build Process:**
Start the build process by running the following command. This step can take several hours depending on your machine's performance.
bitbake core-image-minimal

**Use Balena Etcher:**
Download and install Balena Etcher, a tool for flashing SD cards.

**Flash the Image:**

Open Balena Etcher.
Select the Yocto image(core-image-minimal-raspberrypi5-20240715204324.rootfs.wic) you generated.
Select the SD card as the target.
Click "Flash" to write the image to the SD card.
