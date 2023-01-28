---
title: Wireshark
category: CLI
layout: 2017/sheet
updated: 2020-12-05
keywords:
  - wireshark
intro: |
  Wireshark is an essential tool for network administrators, but very few of them get to unleash its full potential.
---

## Basics
{: .-three-column}

### Controls / Logic
#### Logical Operators

| **Operator**    | **Description**    | **Example**                                                                  |
| --------------- | ------------------ | ---------------------------------------------------------------------------- |
| **and or &&**   | Logical AND        | All the conditions should match                                              |
| **or or ||**    | Logical OR         | Either all or one of the conditions should match                             |
| **xor or ^^**   | Logical XOR        | Exclusive alterations – only one of the two conditions should match not both |
| **not or !**    | Not (Negation)     | Not equal to                                                                 |
| **[ n ] [ … ]** | Substring operator | Filter a specific word or text|

#### Filtering Packets (Display Filters)
| ****Operator**** | ****Description****   | **Example**               |
| ---------------- | --------------------- | ------------------------- |
| **eq or ==**     | Equal                 | ip.dest  ==  192.168.1.1  |
| **ne or !=**     | Not equal             | ip.dest  !=   192.168.1.1 |
| **gt or >**      | Greater than          | frame.len   >   10        |
| **it or <**      | less than             | frame.len  <   10         |
| **ge or >=**     | Greater than or equal | frame.len  >=   10        |
| **le or <=**     | Less than or equal    | frame.len  <=   10        |

#### Filter Types
Capture filter	- Filter packets during capture  
Display filter	- Hide packets from a capture display

#### Wireshark Capturing Modes
Promiscuous mode	- Sets interface to capture all packets on a network segment to which it is associated to  
Monitor mode	- Setup the wireless interface to capture all traffic it can receive (Unix/ Linux only)


#### Good to know
Slice Operator	[ … ] – Range of values  
Membership Operator	{} – In  
CTRL+E	Start/Stop Capturing  
No.	- Frame number from the beginning of the packet capture  
Time	- Seconds from the first frame  
Source (src)	- Source address, commonly an IPv4, IPv6 or Ethernet address  
Destination (dst)	- Destination address  
Protocol	- Protocol used in the Ethernet frame, IP packet, or TC segment  
Length	- Length of the frame in bytes  


Capture Filter Syntax
| **Syntax** | **Protocol** | **Direction** | **Hosts**   | **Value** | **Logical Operator** | ****Expressions****  |
| ---------- | ------------ | ------------- | ----------- | --------- | -------------------- | -------------------- |
| Capture Filter Syntax    | tcp          | src           | 192.168.1.1 | 80        | and                  | tcp dst 202.164.30.1 |


| **Syntax** | **Protocol** | **String 1** | **String 2** | **Comparison Operator** | **Value**   | **Logical Operator** | **Expressions** |
| ---------- | ------------ | ------------ | ------------ | ----------------------- | ----------- | -------------------- | --------------- |
| Display Filter Syntax    | http         | dest         | ip           | \==                     | 192.168.1.1 | and                  | tcp port        |

### Keyboard

| **Accelerator**      | **Description**                                                                               | **Accelerator**      | **Description**                                                              |
| -------------------- | --------------------------------------------------------------------------------------------- | -------------------- | ---------------------------------------------------------------------------- |
| **Tab or Shift+Tab** | Move between screen elements, e.g. from the toolbars to the packet list to the packet detail. | **Alt+→ or Option→** | Move to the next packet in the selection history.                            |
| **↓**                | Move to the next packet or detail item.                                                       | **→**                | In the packet detail, opens the selected tree item.                          |
| **↑**                | Move to the previous packet or detail item.                                                   | **Shift+→**          | In the packet detail, opens the selected tree items and all of its subtrees. |
| **Ctrl+ ↓ or F8**    | Move to the next packet, even if the packet list isn’t focused.                               | **Ctrl+→**           | In the packet detail, opens all tree items.                                  |
| **Ctrl+ ↑ Or F7**    | Move to the previous packet, even if the packet list isn’t focused                            | **Ctrl+←**           | In the packet detail, closes all the tree                                    |
| **Ctrl+.**           | Move to the next packet of the conversation (TCP, UDP or IP).                                 | **Backspace**        | In the packet detail, jumps to the parent node.                              |
| **Ctrl+,**           | Move to the previous packet of the conversation (TCP, UDP or IP).                             | **Return or Enter**  | In the packet detail, toggles the selected tree item.                        |

### Common filters / commands

| **Usage**                        | **Filter Syntax**                                 |
| -------------------------------- | ------------------------------------------------- |
| **Wireshark Filter by IP**       | ip.add == 10.10.50.1                              |
| **Filter by Destination IP**     | ip.dest == 10.10.50.1                             |
| **Filter by Source IP**          | ip.src == 10.10.50.1                              |
| **Filter by IP range**           | ip.addr >= 10.10.50.1 and ip.addr <=10.10.50.100  |
| **Filter by Multiple Ips**       | ip.addr == 10.10.50.1 and ip.addr == 10.10.50.100 |
| **Filter out IP adress**         | ! (ip.addr == 10.10.50.1)                         |
| **Filter subnet**                | ip.addr == 10.10.50.1/24                          |
| **Filter by port**               | tcp.port == 25                                    |
| **Filter by destination port**   | tcp.dstport == 23                                 |
| **Filter by ip adress and port** | ip.addr == 10.10.50.1 and Tcp.port == 25          |
| **Filter by URL**                | http.host == “host name”                          |
| **Filter by time stamp**         | frame.time >= “June 02, 2019 18:04:00”            |
| **Filter SYN flag**              | Tcp.flags.syn == 1 and tcp.flags.ack ==0          |
| **Wireshark Beacon Filter**      | wlan.fc.type_subtype = 0x08                       |
| **Wireshark broadcast filter**   | eth.dst == ff:ff:ff:ff:ff:ff                      |
| **Wireshark multicast filter**   | (eth.dst[0] & 1)                                  |
| **Host name filter**             | ip.host = hostname                                |
| **MAC address filter**           | eth.addr == 00:70:f4:23:18:c4                     |
| **RST flag filter**              | tcp.flag.reset == 1                               |

### More / todo

https://packetlife.net/media/library/12/tcpdump.pdf  
https://packetlife.net/media/library/13/Wireshark_Display_Filters.pdf