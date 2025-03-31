
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

## Device Info

### Get UDBox SN

| **Description**      | Get UDB-0630 SN    |
|----------------------|--------------------|
| **R/W**              | Read               |
| **Command**          | GET_UDBOX_SN\r\n   |
| **Response Example** | UDB-2445031-0630\r\n |

### Get UD module SN

| **Description**      | Get UDB Module part SN    |
|----------------------|--------------------|
| **R/W**              | Read               |
| **Command**          | GET_MODULE_SN\r\n   |
| **Response Example** | UDB-2445031-0630\r\n |

### Get HW version

| **Description**      | Get HW version    |
|----------------------|--------------------|
| **R/W**              | Read               |
| **Command**          | GET_HW_VER\r\n   |
| **Response Example** | 2.1.5.0\r\n |

### Get FW verion

| **Description**      | Get FW version    |
|----------------------|--------------------|
| **R/W**              | Read               |
| **Command**          | GET_FW_VER\r\n   |
| **Response Example** | 1.0.1.0\r\n |

### Get LO Freq Capability

| **Description**      | Get LO Freq(Hz) Capability(min, max)    |
|----------------------|--------------------|
| **R/W**              | Read               |
| **Command**          | GET_LO_CAPABILITY\r\n   |
| **Response Example** | 6000000000,30000000000\r\n |

### Get LO Freq Avilable Range

| **Description**      | Get current LO Freq(Hz) Avilable Range(min, max), it can be extended via unlock license    |
|----------------------|--------------------|
| **R/W**              | Read               |
| **Command**          | GET_LO_RANGE\r\n   |
| **Response Example** | 6000000000,10000000000\r\n |

### Get All Status

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

## System Config

### Get Static IP

| **Description**      | Get static IP    |
|----------------------|--------------------|
| **R/W**              | Read               |
| **Command**          | GET_STATIC_IP\r\n   |
| **Response Example** | 192.168.100.113\r\n |

### Set Static IP

| **Description**      | Set static IP, it needs reboot to makes effect    |
|----------------------|--------------------|
| **R/W**              | Write               |
| **Command**          | SET_STATIC_IP {IP}\r\n   |
| **Command Example**  | SET_STATIC_IP 192.168.1.1\r\n |
| **Response Example** | 0\r\n |

## UD Config

### Get LO Frequency

| **Description**      | Get LO Frequency(Hz)    |
|----------------------|--------------------|
| **R/W**              | Read               |
| **Command**          | GET_LO_FREQ\r\n   |
| **Response Example** | 8500000000\r\n |

### Set LO Frequency

| **Description**      | Set LO Frequency(Hz)    |
|----------------------|--------------------|
| **R/W**              | Write               |
| **Command**          | SET_LO_FREQ {Freq}\r\n   |
| **Command Example**  | SET_LO_FREQ 8500000000\r\n |
| **Response Example** | 0\r\n |

### Get LO External Config

| **Description**      | Get LO external Config    |
|----------------------|--------------------|
| **R/W**              | Read               |
| **Command**          | GET_LO_CONFIG\r\n   |
| **Response Example** | 0\r\n |

- LO config
  - 0: LO internal
  - 1: LO internal output
  - 2: LO external input

### Set LO External Config

| **Description**      | Set LO external Config    |
|----------------------|--------------------|
| **R/W**              | Write               |
| **Command**          | SET_LO_CONFIG {config}\r\n   |
| **Command Example**  | SET_LO_CONFIG 1\r\n |
| **Response Example** | 0\r\n |

- LO config
  - 0: LO internal
  - 1: LO internal output
  - 2: LO external input

### Get Reference Config

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

### Set Reference Config

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

### Get

| **Description**      | Get     |
|----------------------|--------------------|
| **R/W**              | Read               |
| **Command**          | \r\n   |
| **Response Example** | \r\n |

## License

### Set License Key

| **Description**      | Set license key    |
|----------------------|--------------------|
| **R/W**              | Write               |
| **Command**          | SET_LIC_KEY {key from sales}\r\n   |
| **Command Example**  | SET_REF_CONFIG 808d5b00002d31010647a88299153a16404073215d69a6936ce49c69d48055ed354c58a1f563b241\r\n |
| **Response Example** | 0\r\n |
