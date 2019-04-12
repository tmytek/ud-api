
# UART Packet Format of TMYTEK UD Box
![](https://d2mxuefqeaa7sj.cloudfront.net/s_182B9C2A5F3E602310842AB2F88AFF8B53760ED3CBBBB56826875F966CBAD3F9_1538119421184_Phi-A_to_BBrain_comunication.png)

Both Tx/Rx packets follows the format showed above.
The packet length is 10 bytes.
# Length
The length is counting from frame header to checksum.

# Cmd type

## 0x00
The packet returned from UD Box to denote UD recived “correct” command format.
## 0x01
### Function: Set frequency in kHz resolution
### Data payload
* Low byte of target frequency in kHz
* Mid byte of target frequency in kHz
* High byte of target frequency in kHz
* Highest byte of target frequency in kHz
* For the future developed 
## 0x02
### Function: Set default frequency 
### Data payload
* Low byte of target frequency in kHz
* Mid byte of target frequency in kHz
* High byte of target frequency in kHz
* Highest byte of target frequency in kHz
* For the future developed 

## 0xFF
The packet returned from UD Box to denote UD recived “incorrect” command format.

## LRC
For every Tx pakcet user needs to prepare LRC checksum before sending the command to UD Box.
The LRC is generated by frame header and data payload only.

pseudo code

```
uint8_t LRC(uint8_t *msgPtr, uint8_t len)
{
  uint8_t mLRC = 0;
  for each element in msgPtr
  {
    mLRC += each element in msgPtr
  }
  return ((uint8_t)(-((uint8_t)mLRC))); // two's complement
}
```