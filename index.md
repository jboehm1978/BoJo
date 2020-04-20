Title:␣␣␣␣MultiMarkdown-CheatSheet␣␣
Date:␣␣␣␣␣2020-03-30␣␣
Author:␣␣␣Johannes Böhm, Janek Filus, 

# byteWIKI V1.0 
## Welcome to the byteWIKI of bytes at work AG!

<span style="color:dodgerblue">__The byteWIKI__</span> provides important und helpful information related to our products. The byteWIKI is constantly updated with the newest Software- and Hardware-Versions. The byteWIKI ensures a clear overview of all necessary connections. Furthermore, you will find information how to create a bootable SD-Card with a prebuilt image by bytesatwork and how to install the prebuilt toolchain with an example. It also delivers links to the provided Yocto-layers.

It is splitted into four different sections:
[First Start](#first-start) / [Hardware Preparation](#hardware-preparation) / [Software Development](#software-development) / [Hardware Development](#hardware-development)
- - - -
| **Rev. History:** |
|:------------------|
| *_30.03.20: First Edition_*|
- - - -
## Table of contents
- [First Start](#first-start)
- [Hardware Preparation](#hardware-preparation)
- [Software Development](#software-development)
  * [1. Where do you get the toolchain?](#gettingtoolchain)
	+ [1.1 byteDEVKIT](#1.1-bytedevkit)
	+ [1.2 bytePANEL](#1.2-bytepanel)
  * [2. Where do you get the Image for your SD-Card?](#gettingimage)
	+ [2.1 byteDEVKIT](#2.1-bytedevkit)
	+ [2.2 bytePANEL](#2.2-bytepanel)
  * [3. How do you flash the Image?](#flashingimage)
	+ [3.1 byteDEVKIT](#3.1-bytedevkit)
	+ [3.2 bytePANEL](#3.2-bytepanel)
  * [4. How do you build an Image?](#buildingimage)
	+ [4.1 byteDEVKIT](#4.1-bytedevkit)
	+ [4.2 bytePANEL](#4.2-bytepanel)
  * [5. How do you build a toolchain?](#buildingtoolchain)
	+ [5.1 byteDEVKIT](#5.1-bytedevkit)
  * [6. How do you install the toolchain?](#installingtoolchain)
	+ [6.1 byteENGINE AM335x](#6.1-byteengine-am335x)
	+ [6.2 byteENGINE STM32MP1x](#6.2-byteengine-stm32mp1x)
  * [7. How do you use the toolchain?](#usingtoolchain)
	+ [7.1 byteENGINE AM335x](#7.1-byteengine-am335x)
	+ [7.2 byteENGINE STM32MP1x](#7.2-byteengine-stm32mp1x)
- [Hardware Development](#hardware-development)
  * [byteENGINE AM335x](#byteengine-am335x)
  * [byteENGINE STM32MP1x](#byteengine-stm32mp1x)


______

## First Start
This describes the initial startup of the SOM, dev-Kit.

## Hardware Preparation
Essential preparations for the first startup of the SOM, dev-kit.
* Picture 1: ![Alt-Text](pfad/bild.png)
* Picture 2: ![Alt-Text](pfad/bild.png)
* Picture 3: ![Alt-Text](pfad/bild.png)

<a href="http://www.youtube.com/watch?feature=player_embedded&v=F-7W6coaK70&t=1s
" target="_blank"><img src="http://i3.ytimg.com/vi/F-7W6coaK70/hqdefault.jpg" 
alt="bytesatwork AG" width="240" height="180" border="10" /></a>

## Software Development
### 1. Where do you get the toolchain? <a name="gettingtoolchain"></a>
#### 1.1 byteDEVKIT <a name="1.1-bytedevkit"></a>
* **Yocto 3.0**
MISSING Data

* **Yocto 2.7**
MISSING Data

#### 1.2 bytePANEL <a name="1.2-bytepanel"></a>
* **Yocto 3.0**<br/>
	_Download LINK_: <https://bytesatwork.ch/downloads/transfer/bytesatwork/poky-bytesatwork-glibc-x86_64-devbase-image-bytesatwork-armv7at2hf-neon-bytepanel-toolchain-3.0.1.sh>

* **Yocto 2.7**<br/>
	_Download LINK_: <https://bytesatwork.ch/downloads/transfer/bytesatwork/poky-bytesatwork-glibc-x86_64-devbase-image-bytesatwork-armv7at2hf-neon-bytepanel-toolchain-2.7.3.sh>

### 2. Where do you get the Image for your SD-Card? <a name="gettingimage"></a>

#### 2.1 byteDEVKIT <a name="2.1-bytedevkit"></a>
* **Yocto 3.0**
MISSING Data

* **Yocto 2.7**
MISSING Data

#### 2.2 bytePANEL <a name="2.2-bytepanel"></a>
* **Yocto 3.0**<br/>
	_Download LINK_: <https://bytesatwork.ch/downloads/transfer/bytesatwork/devbase-image-bytesatwork-bytepanel.wic.gz>

* **Yocto 2.7**<br/>
	_Downlad LINK_: <https://bytesatwork.ch/downloads/transfer/bytesatwork/m2/2.7/devbase-image-bytesatwork-bytepanel-emmc-20190729194430.sdimg.gz>

### 3. How do you flash the Image? <a name="flashingimage"></a>

#### 3.1 byteDEVKIT <a name="3.1-bytedevkit"></a>
* **Yocto 3.0**
* **Yocto 2.7**

#### 3.2 bytePANEL <a name="3.2-bytepanel"></a>
* **Yocto 3.0**
* **Yocto 2.7**

### 4. How do you build an Image? <a name="buildingimage"></a>
#### 4.1 byteDEVKIT <a name="4.1-bytedevkit"></a>
* **Yocto 2.7 & Yocto 3.0**

	Use repo to download all necessary repositories:
	```
	repo init -u https://github.com/bytesatwork/bsp-platform-st.git -b warrior repo sync
	```

	If those commands are completed successfully, the following command will setup a Yocto Project environment for byteDEVKIT:
	```
	MACHINE=bytedevkit DISTRO=poky-bytesatwork EULA=1 . setup-environment build
	```

	The final command builds the development image:
	```
	bitbake devbase-image-bytesatwork
	```

	The output is found in:
	```
	tmp/deploy/images/bytedevkit
	```

#### 4.2 bytePANEL <a name="4.2-bytepanel"></a>
* **Yocto 2.7 & Yocto 3.0**

	Use repo to download all necessary repositories:
    ```
    repo init -u https://github.com/bytesatwork/bsp-platform.git -b zeus repo sync
    ```

	If those commands are completed successfully, the following command will setup a Yocto Project environment for bytePANEL:
    ```
    MACHINE=bytepanel DISTRO=poky-bytesatwork EULA=1 . setup-environment build
    ```

	the final command builds the development image:
    ```
    bitbake devbase-image-bytesatwork
    ```

	The output is found in:
    ```
    tmp/deploy/images/bytepanel
    ```

### 5. How do you build a toolchain? <a name="buildingtoolchain"></a>

#### 5.1 byteDEVKIT <a name="5.1-bytedevkit"></a>
* **Yocto 2.7**
	```
    repo init -u https://github.com/bytesatwork/bsp-platform-st.git -b warrior repo sync
    ```

	If those commands are completed successfully, the following command will setup a Yocto Project environment for byteDEVKIT:
    ```
    MACHINE=bytedevkit DISTRO=poky-bytesatwork EULA=1 . setup-environment build
    ```

	The final command builds an installable toolchain:
    ```
    bitbake devbase-image-bytesatwork -c populate_sdkbytePANEL
    ```

* **Yocto 3.0**
	```
	repo init -u https://github.com/bytesatwork/bsp-platform.git -b zeus repo sync
    ```

	If those commands are completed successfully, the following command will setup a Yocto Project environment for bytePANEL:
    ```
    MACHINE=bytepanel DISTRO=poky-bytesatwork EULA=1 . setup-environment build
    ```

	The final command builds an installable toolchain:
    ```
    itbake devbase-image-bytesatwork -c populate_sdk
    ```

### 6. How do you install the toolchain? <a name="installingtoolchain"></a>
#### 6.1 byteENGINE AM335x <a name="6.1-byteengine-am335x"></a>
* _Download the Toolchain and install it_
	```
    sudo ./poky-bytesatwork-glibc-x86_64-devbase-image-bytesatwork-armv7at2hf-neon-bytepanel-toolchain-3.0.1.sh
    ```

#### 6.2 byteENGINE STM32MP1x <a name="6.2-byteengine-stm32mp1x"></a>
* _Download the Toolchain and install it_
	```
    sudo ./poky-bytesatwork-glibc-x86_64-devbase-image-bytesatwork-cortexa7t2hf-neon-vfpv4-bytedevkit-toolchain-2.7.2.sh
    ```

### 7. How do you use the toolchain? <a name="usingtoolchain"></a>
#### 7.1 byteENGINE AM335x <a name="7.1-byteengine-am335x"></a>
Source the Toolchain
```
source /opt/poky-bytesatwork/3.0.1/environment-setup-armv7at2hf-neon-poky-linux-gnueabi
``` 
Check if Cross-compiler is available in environment:
```
echo $CC
```
```
arm-poky-linux-gnueabi-gcc -march=armv7-a -mthumb -mfpu=neon -mfloat-abi=hard
```
```
--sysroot=/opt/poky-bytesatwork/3.0.1/sysroots/armv7at2hf-neon-poky-linux-gnueabi
```	
Crosscompile the source code, e.g. by:
```
$CC helloworld.c -o helloworld
```    

Check generated binary:
```	
file helloworld
```
```
helloworld: ELF 32-bit LSB pie executable, ARM, EABI5 version 1
```

#### 7.2 byteENGINE STM32MP1x <a name="7.2-byteengine-stm32mp1x"></a>
Source the installed Toolchain:
	
```
source /opt/poky-bytesatwork/2.7.2/environment-setup-cortexa7t2hf-neon-vfpv4-poky-linux-gnueabi
```

Check if Cross-compiler is available in environment:
```
echo $CC
```
```
arm-poky-linux-gnueabi-gcc -mthumb -mfpu=neon-vfpv4 -mfloat-abi=hard
```
```
-mcpu=cortex-a7
```
```
--sysroot=/opt/poky-bytesatwork/2.7.2/sysroots/cortexa7t2hf-neon-vfpv4-poky-linux-gnueabi
```
   
Crosscompile the source code, e.g. by:
```
$CC helloworld.c -o helloworld
```

Check generated binary:
```
file helloworld
```
```
helloworld: ELF 32-bit LSB pie executable, ARM, EABI5 version 1
```

## Hardware Development

### byteENGINE AM335x

* **General Information**: The byteENGINE AM335x is a high performance industrial oriented computing module. It allows a short time-to-market, while reducing development costs and substantial design risks. The system on module (SOM) uses the Texas Instruments AM335x industrial applications processor family. The AM335x features a PowerVRTM SGX Graphics Accelerator Subsystem for 3D graphics acceleration. The Programmable Real-Time Unit and Industrial Communication Subsystem (PRU-ICSS) allows independent operation from the ARM processor. PRU-ICSS enables real-time protocols such as EtherCAT, PROFINET, EtherNet/IP, PROFIBUS, Ethernet Powerlink and Sercos.

	**The byteENGINE AM335x** is a high performance industrial oriented computing module. It allows a short time-to-market, while reducing development costs and substantial design risks.

	**The system on module (SOM)** uses the Texas Instruments AM335x industrial applications processor family. The AM335x features a PowerVRTM SGX Graphics Accelerator Subsystem for 3D graphics acceleration. The Programmable Real-Time Unit and Industrial Communication Subsystem (PRU-ICSS) allows independent operation from the ARM processor. PRU-ICSS enables real-time protocols such as EtherCAT, PROFINET, EtherNet/IP, PROFIBUS, Ethernet Powerlink and Sercos.

* **Pinout AM335x**<br/>
<https://www.bytesatwork.io/wp-content/uploads/2019/03/Datasheet_byteENGINE_AM335x-12.pdf>

### byteENGINE STM32MP1x

* **General Information**: The byteENGINE STM32MP1x is a high performance industrial oriented computing module. It allows you a short time-to-market, reducing development costs and substantial design risks.

	**The system on module (SOM)** uses the STM32MP15xxAC devices which are based on the high-performance dual-core ARM® Cortex®-A7 32-bit RISC core operating at up to 650 MHz/800 MHz. The STM32MP15xxAC devices also embed a Cortex®-M4 32-bit RISC core operating at up to 200 MHz frequency. The Cortex®-M4 core features a floating point unit (FPU) single precision which supports ARM® single-precision dataprocessing instructions and data types.

	**Furthermore, the STM32MP15xxAC** devices embed a 3D graphic processing unit (Vivante® - OpenGL® ES 2.0) running at up to 533 MHz, with performances up to 26 Mtriangle/s, 133 Mpixel/s.

* **Fact Sheet STM32MP1**<br/><https://www.bytesatwork.io/wp-content/uploads/2019/04/Fact-Sheet-byteENGINE_STM32MP1x.pdf>

+ **Pinout STM32MP1x**<br/><https://www.bytesatwork.io/wp-content/uploads/2019/12/Datasheet_byteENGINE_STM32MP1x-6.pdf>
