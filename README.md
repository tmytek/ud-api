
Control Packet Format
![](https://d2mxuefqeaa7sj.cloudfront.net/s_182B9C2A5F3E602310842AB2F88AFF8B53760ED3CBBBB56826875F966CBAD3F9_1538119421184_Phi-A_to_BBrain_comunication.png)


cmd type :

- 0x00
  Generally using in response packet, it means that the MCU received the “correct” command.
- 0x01
  - set frequency and without saving  to EEPROM
  - 3 bytes of data payload,  | low byte of frequency | high byte of frequency | Nth in frequency table |
- 0x02
  - save frequency to EEPROM without setting frequency
  - 3 bytes of data payload,  | low byte of frequency | high byte of frequency | Nth in frequency table |
- 0x03
  - read frequency from table then setting frequency
  - 3 bytes of data payload,  | 0x00 | 0x00 | Nth in frequency table |
- 0xFF
  Generally using in response packet, it means that the MCU received the “incorrect” command.
