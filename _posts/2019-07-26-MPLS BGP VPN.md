---
layout:     post
title:      MPLS BGP VPN
subtitle:   
date:       2019-07-26
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

## 五、CE路由器需要注入Loopback接口

可以通过Import-route direct或者network X.X.X.X 掩码

     [CE-1]bgp 10
     [CE-1-bgp]Import-route direct

## 六、引入VPN路由

     [PE-1-bgp-huawei]Import-route direct
     
## 七、结果

![QQ截图20190811231337.jpg](https://i.loli.net/2019/08/11/rihl4eXC6KJFu2I.jpg)

[![exPpvR.jpg](https://s2.ax1x.com/2019/08/11/exPpvR.jpg)](https://imgchr.com/i/exPpvR)

