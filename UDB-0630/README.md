
# SCPI Command Format of TMYTEK UDB-0630

## Basic Test environment

### TCP socket programming

Programming via Python, C, C++, C##...etc

### Packet Sender

![pkt](/images/packet_sender.png)

- Download/install Packet Sender https://packetsender.com/
- Fill **Name** for usage
- Copy the following command into **ASCII** field
- Press **HEX** field to update from **ASCII** field
- Default static IP: **192.168.100.113**
- Port: **5025**
- TCP

## Quick Link

- [Device Info](#device-info)
  - [Get UDBox SN](#get-udbox-sn)
  - [Get UD Module SN](#get-ud-module-sn)
  - [Get HW version](#get-hw-version)
  - [Get FW verion](#get-fw-verion)
  - [Get LO Freq Capability](#get-lo-freq-capability)
  - [Get LO Freq Available Range](#get-lo-freq-available-range)
  - [Get All Status](#get-all-status)
- [System Config](#system-config)
  - [Get Static IP](#get-static-ip)
  - [Set Static IP](#set-static-ip)
  - [Get Subnet Mask](#get-subnet-mask)
  - [Set Subnet Mask](#set-subnet-mask)
  - [Get Gateway IP](#get-gateway-ip)
  - [Set Gateway IP](#set-gateway-ip)
  - [Get IP Mode](#get-ip-mode)
  - [Set IP Mode](#set-ip-mode)
  - [System Reboot](#system-reboot)
  - [System Preset](#system-preset)
- [UD Config](#ud-config)
  - [Get LO Frequency](#get-lo-frequency)
  - [Set LO Frequency](#set-lo-frequency)
  - [Get LO External Config](#get-lo-external-config)
  - [Set LO External Config](#set-lo-external-config)
  - [Get Reference Config](#get-reference-config)
  - [Set Reference Config](#set-reference-config)
- [License](#license)
  - [Set License Key](#set-license-key)

### Device Info

#### Get UDBox SN

| **Description**      | Get UDB-0630 SN    |
|----------------------|--------------------|
| **R/W**              | Read               |
| **Command**          | GET_UDBOX_SN\r\n   |
| **Response Example** | UDB-2445031-0630\r\n |

#### Get UD Module SN

| **Description**      | Get UD module part SN    |
|----------------------|--------------------|
| **R/W**              | Read               |
| **Command**          | GET_MODULE_SN\r\n   |
| **Response Example** | UDB-2445031-0630\r\n |

#### Get HW version

| **Description**      | Get HW version    |
|----------------------|--------------------|
| **R/W**              | Read               |
| **Command**          | GET_HW_VER\r\n   |
| **Response Example** | 2.1.5.0\r\n |

#### Get FW verion

| **Description**      | Get FW version    |
|----------------------|--------------------|
| **R/W**              | Read               |
| **Command**          | GET_FW_VER\r\n   |
| **Response Example** | 1.0.1.0\r\n |

#### Get LO Freq Capability

| **Description**      | Get LO freq(Hz) capability(min, max)    |
|----------------------|--------------------|
| **R/W**              | Read               |
| **Command**          | GET_LO_CAPABILITY\r\n   |
| **Response Example** | 6000000000,30000000000\r\n |

#### Get LO Freq Available Range

| **Description**      | Get current LO freq(Hz) available range(min, max), it can be extended via unlock license    |
|----------------------|--------------------|
| **R/W**              | Read               |
| **Command**          | GET_LO_RANGE\r\n   |
| **Response Example** | 6000000000,10000000000\r\n |

#### Get All Status

| **Description**      | Get device all status include System, LO, Reference and License     |
|----------------------|--------------------|
| **R/W**              | Read               |
| **Command**          | GET_ALL_STATUS\r\n   |
| **Response Example** | 0,0,0,1\r\n |

- System
  - 0: normal
  - 1: error
- LO
  - 0: locked
  - 1: unlocked
- Reference
  - 0x00: internal locked
  - 0x01: external locked
  - 0x11: unlocked
- License
  - 0x00: not exist
  - 0x01: verify success
  - 0x11: verify failed
  - 0x12: read error

### System Config

#### Get Static IP

| **Description**      | Get static IP    |
|----------------------|--------------------|
| **R/W**              | Read               |
| **Command**          | GET_STATIC_IP\r\n   |
| **Response Example** | 192.168.100.113\r\n |

#### Set Static IP

| **Description**      | Set static IP, it needs reboot to makes effect    |
|----------------------|--------------------|
| **R/W**              | Write               |
| **Command**          | SET_STATIC_IP {IP}\r\n   |
| **Command Example**  | SET_STATIC_IP 192.168.1.1\r\n |
| **Response Example** | 0\r\n |

#### Get Subnet Mask

| **Description**      | Get subnet mask    |
|----------------------|--------------------|
| **R/W**              | Read               |
| **Command**          | GET_SUBNET_MASK\r\n   |
| **Response Example** | 255.255.255.0\r\n |

#### Set Subnet Mask

| **Description**      | Set subnet mask, it needs reboot to makes effect    |
|----------------------|--------------------|
| **R/W**              | Write               |
| **Command**          | SET_SUBNET_MASK {mask}\r\n   |
| **Command Example**  | SET_SUBNET_MASK 255.255.255.0\r\n |
| **Response Example** | 0\r\n |

#### Get Gateway IP

| **Description**      | Get gateway IP    |
|----------------------|--------------------|
| **R/W**              | Read               |
| **Command**          | GET_GATEWAY\r\n   |
| **Response Example** | 192.168.100.254\r\n |

#### Set Gateway IP

| **Description**      | Set gateway IP, it needs reboot to makes effect    |
|----------------------|--------------------|
| **R/W**              | Write               |
| **Command**          | SET_GATEWAY {gateway}\r\n   |
| **Command Example**  | SET_GATEWAY 192.168.100.254\r\n |
| **Response Example** | 0\r\n |

#### Get IP Mode

| **Description**      | Get IP obtain mode, obtaining IP from DHCP or Static IP    |
|----------------------|--------------------|
| **R/W**              | Read               |
| **Command**          | GET_IP_MODE\r\n   |
| **Response Example** | 0\r\n |

- IP Mode
  - DHCP
  - Static IP

#### Set IP Mode

| **Description**      | Set gateway IP, it needs reboot to makes effect    |
|----------------------|--------------------|
| **R/W**              | Write               |
| **Command**          | SET_IP_MODE {ip_mode}\r\n   |
| **Command Example**  | SET_IP_MODE 0\r\n |
| **Response Example** | 0\r\n |

- IP Mode
  - DHCP
  - Static IP

#### System Reboot

| **Description**      | Reboot the system   |
|----------------------|--------------------|
| **R/W**              | Write               |
| **Command**          | SYS_REBOOT\r\n   |
| **Response Example** | N/A |

#### System Preset

| **Description**      | Recovery to RF/UD default config only   |
|----------------------|--------------------|
| **R/W**              | Write               |
| **Command**          | SYS_PRESET\r\n   |
| **Response Example** | 0\r\n |

### UD Config

#### Get LO Frequency

| **Description**      | Get LO frequency(Hz)    |
|----------------------|--------------------|
| **R/W**              | Read               |
| **Command**          | GET_LO_FREQ\r\n   |
| **Response Example** | 8500000000\r\n |

#### Set LO Frequency

| **Description**      | Set LO frequency(Hz)    |
|----------------------|--------------------|
| **R/W**              | Write               |
| **Command**          | SET_LO_FREQ {Freq}\r\n   |
| **Command Example**  | SET_LO_FREQ 8500000000\r\n |
| **Response Example** | 0\r\n |

#### Get LO External Config

| **Description**      | Get LO external config    |
|----------------------|--------------------|
| **R/W**              | Read               |
| **Command**          | GET_LO_CONFIG\r\n   |
| **Response Example** | 0\r\n |

- LO config
  - 0: LO internal
  - 1: LO internal output
  - 2: LO external input

#### Set LO External Config

| **Description**      | Set LO external config    |
|----------------------|--------------------|
| **R/W**              | Write               |
| **Command**          | SET_LO_CONFIG {config}\r\n   |
| **Command Example**  | SET_LO_CONFIG 1\r\n |
| **Response Example** | 0\r\n |

- LO config
  - 0: LO internal
  - 1: LO internal output
  - 2: LO external input

#### Get Reference Config

| **Description**      | Get reference clock source/destination config    |
|----------------------|--------------------|
| **R/W**              | Read               |
| **Command**          | GET_REF_CONFIG\r\n   |
| **Response Example** | 0\r\n |

- Reference config
  - 0: Ref clock internal
  - 1: Ref clock internal out 10MHz
  - 2: Ref clock internal out 100MHz
  - 3: Ref clock external in 10MHz
  - 4: Ref clock external in 100MHz

#### Set Reference Config

| **Description**      | Set reference clock source/destination config    |
|----------------------|--------------------|
| **R/W**              | Write               |
| **Command**          | SET_REF_CONFIG {config}\r\n   |
| **Command Example**  | SET_REF_CONFIG 2\r\n |
| **Response Example** | 0\r\n |

- Reference config
  - 0: Ref clock internal
  - 1: Ref clock internal out 10MHz
  - 2: Ref clock internal out 100MHz
  - 3: Ref clock external in 10MHz
  - 4: Ref clock external in 100MHz

### License

#### Set License Key

| **Description**      | Set license key    |
|----------------------|--------------------|
| **R/W**              | Write               |
| **Command**          | SET_LIC_KEY {key from sales}\r\n   |
| **Command Example**  | SET_REF_CONFIG 808d5b00002d31010647a88299153a16404073215d69a6936ce49c69d48055ed354c58a1f563b241\r\n |
| **Response Example** | 0\r\n |
