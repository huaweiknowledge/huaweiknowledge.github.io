---
layout:     post
title:      MPLS BGP VPN
subtitle:   
date:       2019-07-29
author:     chauncey
header-img: img/d021cd5db5f453de969fa251d0fe6d56.jpg
catalog: true
tags:
    - 通信协议
---

>>>  MPLS BGP VPN的相关配置

![QQ截图20190811224237.jpg](https://i.loli.net/2019/08/11/lPBmxfycv3arVFJ.jpg)

## 一、IGP配置

配置OSPF协议

## 二、MPLS LDP

分别在系统视图和接口下使能 

     []mpls lsr-id 1.1.1.1
     []mpls
     []mpls ldp

## 三、创建VPN实例

     []ip vpn-instance huawei
     []routinguisher 100:1
     []vpn-target 100:1
     [GigabitEthernet0/0/0]ip binding vpn-instance huawei
     [GigabitEthernet0/0/0]ip address 10.1.1.1 30

## 四、建立PE之间的MP-BGP关系，CE与PE E-BGP关系

     [PE-1]peer 3.3.3.3 as-number 100
     [PE-1]peer 3.3.3.3 connect-interface Loopback 0
     [PE-1-bgp-huawei]peer 10.1.1.2 as-number 10
     [PE-1-bgp-af-vpnv4]peer 3.3.3.3 enable

## 一、

## 一、

## 一、

## 一、

## 一、
