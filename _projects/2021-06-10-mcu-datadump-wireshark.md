---
title: "Mcu Datadump Wireshark"
collection: projects
permalink: /projects/mcu-datadump-wireshark
excerpt: 'A tool dumps datas from mcu to PC and put them into wireshark to analyse.'
date: 2021-06-10
tags:
  - MCU
  - RTOS
  - Wireshark
  - Protocol analysis
---

## Brief

This project is created by me as a component for [OneOS](https://gitee.com/cmcc-oneos/OneOS) to dump data from mcu to pc and analyse data in Wireshark. It can be ported to other RTOS or bare metal system.

---

## Purpose

Sometimes we need to analyse protocol (as BT/ETH/TCPIP/...) used in Mcu, but it is annoying to analyse protocol data by just printing them out in Hecadecimal format or other format. We are used to analyse protocol in GUI tools that can display protocol data with data bit definition. As Wireshark is a great protocol analysing tool and support many protocols, so I decided to build this project to achieve this goal.

---

## Structure
```c
└── wireshark_log
    ├── device
    └── host
```

### device

Software runs in device that you want to dump data from. It output data you want to dump in some frame format to host (PC). 

|  1B  |  2B  |  4B  |  1B  |  NB  |  1B  |
| ---  | ---  | ---  | ---  | ---  | ---  |
| 0xAA | len  | time | dir  | data | 0x55 |

### host

Software runs in PC. It recieces data from device and transport them to wireshark through the Pipe created in initialization process.

---

## How to use on host

### Requirement

* python3
* pyserial
* wireshark
* pywin32 ( Windows )

### Cmd

```shell
python serial_trans.py -h   # Use this cmd to get more information.
```

---

## Repository & Demo

Git repository:  
[github.com/novumdun/mcu-datadump-wireshark](https://github.com/novumdun/mcu-datadump-wireshark)  

Demo:  
[https://youtu.be](https://youtu.be/AR5nKpMRGrU)
