## Installing on Virtual Machine by Building from Source method

---

## Table of Contents
- [Software and Hardware](#id-specification)
- [Installaion Procedure](#id-installation)
- [Network Functions Runing](#id-networkfunction)

---

<div id='id-specification'/>

## Software and Hardware

### Hardware Specification
| Module           | Detail                                         |
| -----------      | -----------                                    |
| Operating System | Windows 11 Home 21H2                           |
| Processer        | 11th Gen Intel(R) Core (TM) i5-1135G7 @2.40GHz |
| RAM              | 16.0 GB                                        |
| Graphics Card    | Intel(R) Iris(R) Xe Graphics                   |
| Connectivity     | Intel(R) Wi-Fi 6 AX201 160MHz                  |

### Software Used
| Software      | Version                 |
| -----------   | -----------             |
| VirsualBox    | VirtualBox 6.1          |
| Open5GS       | Updated Jan, 2022       |
| Ubuntu Server | Ubuntu Server 20.04 LTS |

---

<div id='id-installation'/>

## Installation Procedure

### 1. Create Virtual Machine
| Module      | Detail         |
| ----------- | -----------    |
| Memmory     | 2GB            |
| HDD         | 20GB           |
| Network     | Bridge Adapter |

### 2. Install and Setup Ubuntu Server

Clone this project
~~~ text
cd ~
git clone https://github.com/porrama/install_open5gs
~~~

Run **aptinstall_open5gs.sh**
~~~ text
cd ~/install_open5gs
sudo sh aptinstall_open5gs.sh
~~~

### 3. Install Open5GS software

Clone Open5GS project
~~~ text
cd ~
git clone https://github.com/open5gs/open5gs
~~~

Complie with meson
~~~ text
cd ~/open5gs
meson build --prefix=`pwd`/install
~~~

Ninja build
~~~ text
cd ~/open5gs
ninja -C build
~~~

~~~ text
cd ~/open5gs/build
ninja install
~~~

WebUI Install (Only for Control Plane)
~~~ text
cd ~/open5gs
curl -fsSL https://deb.nodesource.com/setup_14.x | sudo -E bash -
~~~

~~~ text
cd ~/open5gs/webui
npm ci --no-optional
~~~

---

<div id='id-networkfunction'/>

## Network Function Testing

Run **runcorecontrol.sh**
~~~ text
cd ~
sudo sh runcorecontrol.sh
~~~ 

---
