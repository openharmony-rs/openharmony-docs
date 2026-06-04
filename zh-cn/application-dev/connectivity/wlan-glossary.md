# Wi-Fi术语

<!--Kit: Connectivity Kit-->
<!--Subsystem: Communication-->
<!--Owner: @qq_43802146-->
<!--Designer: @qq_43802146-->
<!--Tester: @furryfurry123-->
<!--Adviser: @zhang_yixin13-->

## B

### BSSID; 基本服务集标识符
Basic Service Set Identifier。无线网络中用于标识接入点的唯一MAC地址，用于区分不同接入点。

## D

### DHCP; 动态主机配置协议
Dynamic Host Configuration Protocol。自动分配IP等网络配置信息的协议，设备连接[WLAN](#wlan-无线局域网)后通过DHCP获取IP地址。

### DNS; 域名系统
Domain Name System。将域名解析为IP地址的系统，是互联网的基础服务之一。

## E

### EAP; 可扩展身份验证协议
Extensible Authentication Protocol。用于网络认证的框架协议，支持多种认证方式（PEAP、TLS、TTLS等）。

## G

### GroupOwnerBand; 群组频段
P2P连接中群组所使用的工作频段。包括自动模式（GO_BAND_AUTO）、2.4GHz频段（GO_BAND_2GHZ）和5GHz频段（GO_BAND_5GHZ）三种取值。

## M

### EMLSR; 增强型多链路单天线
Enhanced Multi-link Single Radio。[MLO](#mlo-多链路操作)技术中的一种连接类型，相比MLSR提供更好的频段切换协调和更低的时延。

### MLSR; 多链路单天线
Multi-link Single Radio。[MLO](#mlo-多链路操作)技术中的一种连接类型，设备在多个频段上共享单根天线进行数据传输。

### MLO; 多链路操作
Multi-Link Operation。[Wi-Fi](#wi-fi) 7（802.11be）引入的多频段并发技术，允许设备同时在多个频段上进行数据传输，通过聚合多个链路的带宽提升传输速率和可靠性。

## O

### OWE; 机会性无线加密
Opportunistic Wireless Encryption。针对开放[Wi-Fi](#wi-fi)网络的安全增强机制，自动对开放网络流量进行加密。

## P

### P2P; 点对点
Peer-to-Peer。[WLAN](#wlan-无线局域网)直连技术，允许设备间不通过AP直接建立连接进行数据传输。

### Portal; 强制门户认证
Captive Portal。公共WLAN网络的Web页面认证机制，用于酒店、机场、咖啡厅等场所的身份验证。
Portable Interactive Optical Access Redirector。公共WLAN网络的Web页面认证机制，用于酒店、机场、咖啡厅等场所的身份验证。

### PSK; 预共享密钥
Pre-shared Key。[WLAN](#wlan-无线局域网) WPA/WPA2个人版使用的对称密钥，用户预先在设备和无线路由器上配置相同密码。

## R

### RSSI; 接收信号强度指示
Received Signal Strength Indicator。无线通信中量化接收端信号强度的指标，单位是dBm。

## S

### SAE; 同步认证对等
Simultaneous Authentication of Equals。WPA3-Personal使用的密钥交换协议，解决[PSK](#psk-预共享密钥)易被离线字典攻击的缺陷。

### SSID; 服务集标识符
Service Set Identifier。[Wi-Fi](#wi-fi)网络的名称，用于标识一个无线局域网。

### STA; 工作站
Station。连接到无线网络的终端设备，作为客户端通过AP接入网络。

## W

### WAPI; 无线局域网鉴别与保密基础架构
Wireless LAN Authentication and Privacy Infrastructure。中国制定的无线局域网安全协议标准，采用基于证书的认证机制。

### WLAN; 无线局域网
Wireless Local Area Network。利用无线电波在一定范围内建立网络连接的技术，使设备能够以无线方式接入网络。

### WEP; 有线等效加密
Wired Equivalent Privacy。早期[WLAN](#wlan-无线局域网)加密协议，安全性存在严重漏洞，已被WPA/WPA2取代。

### Wi-Fi
基于[WLAN](#wlan-无线局域网)技术的无线通信品牌名称，由Wi-Fi联盟维护和认证，遵循IEEE 802.11标准系列。

### WPA; Wi-Fi保护访问
Wi-Fi Protected Access。[WLAN](#wlan-无线局域网)安全协议标准，作为[WEP](#wep-有线等效加密)的替代方案。

### WPA2; Wi-Fi保护访问第二代
Wi-Fi Protected Access II。WPA的升级版本，引入AES加密算法替代TKIP，提供更强的安全性。

### WPA3; Wi-Fi保护访问第三代
Wi-Fi Protected Access III。最新[Wi-Fi](#wi-fi)安全标准，支持SAE密钥交换协议，提供更强的加密算法和更安全的认证机制。