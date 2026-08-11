# Telephony Kit术语
<!--Kit: Telephony Kit-->
<!--Subsystem: Telephony-->
<!--Owner: @shao-yikai-->
<!--Designer: @wnazgul-->
<!--Tester: @jiang_99-->
<!--Adviser: @zhang_yixin13-->

## A

### Abbreviated Dialling Numbers (ADN)；缩位拨号

存储在SIM卡电话簿文件中的联系人条目，每条含名称与号码，是卡上通用电话簿的标准实现，与固定拨号（FDN）相对。

### Absolute Radio Frequency Channel Number (ARFCN)；绝对无线频率信道号

GSM/UMTS中标识载波频点的整数编号，结合频段指示可换算载波绝对频率，用于 2G/3G 网络频点扫描与小区接入。

### Access Point Name (APN)；接入点名称

移动通信中标识分组数据网络接入点的字符串，终端建立蜂窝数据连接时必须配置，决定设备经哪个网关接入运营商网络或专网。

### Activation Code；激活码

eSIM配置文件下载流程中由运营商提供的标识串，配合确认码向SM-DP+服务器发起下载请求；不基于激活码的配置文件该字段可为空。

## B

### Base Station Identity Code (BSIC)；基站识别号

GSM中区分相邻基站的6位识别码，由网络色码（NCC）与基站色码（BCC）组成，帮助终端在频点相同的小区中区分归属基站。

### Baseband；基带

未经射频调制的低频原始信号及其对应的Modem软硬件处理子系统，基带版本号反映Modem固件版本，决定终端对无线接入技术、频段、协议特性的支持能力。

### Bound Profile Package (BPP)；绑定配置文件包

SM-DP+服务器认证通过后下发的、已与目标eUICC绑定的配置文件包，包含可在eUICC上安装的全部内容，是配置文件下载流程的关键中间产物。

## C

### Call Transfer；呼叫转移

电话系统中将来电按预设条件自动转接至另一号码的功能，分无条件转移、忙线转移、无回复转移、无法访问转移四种类型，用于用户无法接听时将来电转至其他号码。

### Carrier Aggregation (CA)；载波聚合

将多个载波分量聚合使用以扩展带宽和提升峰值速率的技术，是LTE/NR提升吞吐量的关键手段，NetworkState中以isCaActive字段标识其激活状态。

### Cell；小区

蜂窝网络中由单个基站扇区覆盖的无线电区域，是移动网络进行位置管理与切换的最小地理单元，终端通过驻留小区接入网络。

### Cell Broadcast (CB)；小区广播

移动网络向特定地理区域内所有终端同时广播短消息的服务，常用于紧急告警与公共通知，不需知道接收方号码，与点对点短信不同。

### Cell Global Identity (CGI)；小区全球标识

全球唯一标识2G/3G小区的编号，由LAC与CI组合而成，是网络定位终端所在小区的核心参数，在LTE/NR中由ECGI/NCI对应。

### Cellular Data；蜂窝数据

通过移动通信网络（如4G/5G）提供的分组数据业务，区别于Wi-Fi，使设备在无无线局域网时仍可上网，是Telephony Kit的核心管理对象。

### Circuit Switched (CS)；电路交换

蜂窝通信中通过独占专用电路资源承载话音、短信等实时业务的交换方式，与分组交换（PS）相对，传统2G/3G网络主要依靠该方式提供语音业务。

### Code Division Multiple Access (CDMA)；码分多址

以扩频码区分用户的无线多址接入技术，是cdmaOne及CDMA2000系列的空口基础，与GSM/WCDMA体系并存，主要用于北美及部分亚洲运营商网络。

### Concatenated SMS；长短信

内容超过单条SMS最大容量时被拆分为多个分片发送、接收时再合并还原的短信形式，分片通过用户数据头（UDH）携带拼接信息。

### Confirmation Code；确认码

eSIM配置文件下载过程中由运营商提供给用户的一次性校验码，用于在下载与安装阶段向服务器证明用户授权。

## D

### Data SMS；数据短信

携带二进制字节数据而非文本内容的短信，发送时须指定目的端口实现端口寻址，用于终端应用间传输结构化数据（如 WAP Push），与文本短信相区分。

### Default Cellular Data SIM；默认移动数据卡

设备当前用于蜂窝数据业务的指定SIM卡，由slotId标识；双卡设备需指定一张作为默认数据卡，是其他蜂窝数据接口的默认作用对象。

### Dual SIM Dual Active (DSDA)；双卡双待双通

双卡双待（DSDS）V5模式之一，允许两张SIM卡同时处于激活并收发信号的状态，避免一卡通话时另一卡无法接入，依赖射频与基带并行支持。

### Dual SIM Dual Standby (DSDS)；双卡双待

设备支持两张SIM卡同时待机但同一时刻仅一卡进行业务的能力，分V2、V3、V5_TDM、V5_DSDA四种模式，由设备硬件能力决定。

## E

### E-UTRA Absolute Radio Frequency Channel Number (EARFCN)；演进的绝对无线频率信道号

LTE中标识E-UTRA载波频点的编号，由频段指示与频偏确定载波绝对频率，是LTE小区频点描述与测量上报的基础参数。

### E-UTRA NR Dual Connectivity (ENDC)；新无线电双连接

3GPP定义的双连接技术，LTE作为主节点、NR作为辅节点同时为终端提供空口资源，是NSA组网的核心实现方式。

### Embedded SIM (eSIM)；嵌入式SIM卡

以eUICC为载体、可通过SM-DP+远程下载配置文件而无需更换实体卡的SIM形态，区别于可插拔的物理SIM卡。

### Embedded Universal Integrated Circuit Card (eUICC)；嵌入式通用集成电路卡

支持远程配置文件下载、删除、启用的可编程SIM卡硬件，是eSIM的物理载体，其上可驻留多个配置文件，由EID唯一标识。

### Emergency Call；紧急呼叫

在未注册网络或无SIM卡等受限场景下仍允许拨打的特殊呼叫，仅可接入紧急服务号码，是蜂窝网络对终端的最低保障机制。

### Envelope Command；信封命令

SIM应用工具包（USAT）中终端通过ME→UICC通道发送给SIM卡的应用层命令，用于将设备事件（菜单选择、呼叫控制等）传递给卡侧应用，区别于终端响应。

### eUICC Identifier (EID)；eUICC识别码

唯一标识一片eUICC硬件的固定长度码字，作用类似SIM卡的ICCID，但绑定在不可移除的eUICC上。

### Evolution Data Optimized (EVDO)；演进数据优化

CDMA2000 1X EV-DO的简称，专门承载数据业务的CDMA高速分组数据空口，与承担话音的1XRTT分工。

### Evolved High Rate Packet Data (EHRPD)；演进高速率分组数据

HRPD（EVDO）的演进版本，可与LTE核心网EPC互通，使CDMA运营商向LTE演进时保持数据会话连续性。

## F

### Fixed Dialling Number (FDN)；固定拨号

SIM卡中限定只能拨打预设号码列表的电话簿类型，启用后非列表内号码被禁止拨出，与通用联系人（ADN）相对，操作通常需PIN2密码。

## G

### Generic Bootstrapping Architecture (GBA)；通用引导架构

3GPP定义的基于AKA机制在终端与业务服务器间建立共享密钥的引导框架，IMS业务可基于其完成终端与业务网认证。

### Global System for Mobile Communication (GSM)；全球移动通信系统

2G数字蜂窝标准，采用TDMA接入，主要承载CS域话音、短信及低速GPRS/EDGE数据业务，是WCDMA/LTE的演进起点。

### GSM 7-bit；GSM 7位编码

GSM短信默认的字符编码方案，每字符7位，使单条SMS在140字节PDU中可容纳160个字符，仅适用于GSM默认字母表；含非该字母表字符（如中文）时需改用UCS-2编码。

### Group Identifier Level 1 (GID1)；组标识符级别1

存储在SIM卡EF_GID1文件中的标识符，运营商用于区分同一MCC+MNC下不同业务子群，常与GID2组合用于精细化业务路由。

### Group Identifier Level 2 (GID2)；组标识符级别2

存储在SIM卡EF_GID2文件中的次级组标识符，与GID1配合对同一运营商下用户群进行更细粒度划分。

## I

### Integrated Circuit Card (ICC)；集成电路卡

泛指SIM/USIM/UICC等智能卡的通用术语，承载运营商账户与鉴权信息，observer中iccAccountInfoChange事件即基于此命名以统一抽象各类IC卡。

### Integrated Circuit Card Identifier (ICCID)；集成电路卡标识符

SIM/eUICC 卡的唯一识别码，由发卡方写入，含发卡方国家、运营商、序列号、校验位等信息，是 eSIM 配置文件操作的定位键。

### Interworking Wireless LAN (IWLAN)；无线局域网接入

通过WLAN接入EPC/IMS核心网承载VoWiFi等业务的接入方式，使终端在蜂窝信号弱时仍可使用语音和数据业务，作为一种IMS注册技术与3GPP蜂窝接入并列。

### International Mobile Equipment Identity (IMEI)；国际移动设备识别码

3GPP规范定义的15位设备唯一识别码，与SIM卡解耦，用于网络识别终端硬件，运营商可据此进行黑白名单管理。

### International Mobile Equipment Identity - Software Version (IMEISV)；国际移动设备软件版本号

在IMEI基础上附加软件版本号的设备识别码，用于跟踪设备当前固件/软件版本，常用于远程诊断与版本管理。

### International Mobile Subscriber Identity (IMSI)；国际移动用户识别码

3GPP网络中唯一标识移动用户的号码，由MCC、MNC、MSIN组成，存于SIM卡中，是用户身份认证与接入的核心凭据。

### IP Multimedia Services Identity Module (ISIM)；IP多媒体服务身份模块

专为IMS应用设计的SIM卡应用模块，存储IMS用户私有身份（IMPI）、公有身份（IMPU）、家庭网络域名等参数，可独立于USIM存在。

### IP Multimedia Subsystem (IMS)；IP多媒体子系统

3GPP定义的基于IP的多媒体业务控制架构，运行于PS域之上，为VoLTE、VoNR、IMS短信等业务提供注册、会话控制与QoS保障。

## L

### Location Area Code (LAC)；位置区编号

2G/3G CS域中标识位置区的编号，网络通过LAC进行寻呼，终端跨LAC移动时触发位置更新，是CS域移动性管理的基本单位，与PS域的TAC相对应。

### Long Term Evolution (LTE)；长期演进

3GPP R8起定义的4G无线接入技术，采用OFDMA与MIMO提供高速分组数据业务，端到端全IP架构仅保留PS域，是5G NR的锚点与演进基准。

## M

### Mobile Country Code (MCC)；移动国家码

PLMN标识的前3位数字，由ITU分配，用于全球唯一标识移动网络所在国家（如460代表中国），是PLMN、IMSI等的核心组成部分。

### Mobile Equipment Identifier (MEID)；移动设备识别码

CDMA制式设备的14位十六进制唯一识别码，作用与IMEI对应但用于3GPP2网络，是CDMA终端的全球唯一硬件标识。

### Mobile Network Code (MNC)；移动网络码

PLMN标识中跟在MCC之后的2~3位数字，由各国通信管理部门分配，用于区分同一国家内不同运营商，与MCC组合构成完整PLMN。

### Mobile Station International Subscriber Directory Number (MSISDN)；移动台国际用户目录号

存储在SIM卡中的用户电话号码（即主叫号码），以E.164格式表示，与IMSI一一对应但可更换。

### Modem；调制解调器

移动终端中负责蜂窝空口信号处理的硬件子系统及固件，承担调制解调、信道编解码、网络注册等基带功能，Radio开关实际控制其射频上下电状态。

### Multimedia Messaging Service (MMS)；彩信

在移动网络上传输包含文本、图片、音频、视频等多媒体内容消息的业务，与纯文本SMS不同，采用基于WAP/HTTP的PDU封装并经MMSC存储转发。

### Multimedia Messaging Service Center (MMSC)；多媒体消息业务中心

MMS网络中负责存储转发多媒体消息的核心网元，终端发送彩信时将PDU提交至此，由其向接收方下发通知，接收方再检索完整内容。

## N

### Network Identification (NID)；网络识别码

CDMA网络中标识运营商网络区块的编号，与SID组合区分运营商不同子网络，是CDMA网络选择、漫游判断的关键参数。

### New Radio (NR)；新空口

3GPP R15起定义的5G空口标准，工作于Sub-6GHz及毫米波频段，可接入5GC构成SA组网，也可锚定在LTE上以ENDC方式实现NSA组网。

### Next Generation Radio Access Network (NG-RAN)；下一代无线接入网

5G系统的无线接入网架构，由gNB与ng-eNB组成，通过NG接口连接5GC，是SA组网下NR空口的接入网基础。

### Non-Standalone (NSA)；非独立组网

5G NR以LTE为锚点、控制面依赖EPC的部署模式，无需5GC即可提供NR高速数据，是5G商用初期的过渡方案，与SA相对。

### NR Cell Identity (NCI)；5G小区标识

5G NR中全局唯一标识小区的36位编号，由gNB ID与Cell ID组成，是NR网络中定位和标识小区的核心参数，对应2G/3G的CGI与LTE的ECGI。

## O

### Operating System Upgrade (OSU)；eUICC操作系统升级

对eUICC内置操作系统进行版本升级的过程，影响eUICC平台固件本身，区别于配置文件的下载与切换。

### Operator；运营商

提供移动通信网络服务的企业，拥有PLMN并发行SIM卡；Telephony Kit中运营商信息以长/短名称、PLMN码等形式呈现，并影响默认APN配置。

### Operator PLMN List (OPL)；运营商PLMN列表

存储在SIM/eUICC上的运营商自定义PLMN与地理区域映射表，用于网络选择时结合当前位置确定应显示的运营商名称（与PNN配合）。

## P

### Packet Switched (PS)；分组交换

蜂窝通信中以分组为单位按需共享信道资源承载数据业务的交换方式，与电路交换（CS）相对，LTE/NR中所有业务均基于该方式。

### Personal Identification Number (PIN)；个人识别码

保护SIM卡不被未授权使用的本地密码，默认4~8位，连续错误达上限后需PUK解锁，是SIM卡安全体系的第一道防线。

### Personal Unblocking Key (PUK)；个人解锁码

PIN被锁死后用于重置PIN的运营商级解锁码，错误次数达上限将永久锁卡需换卡，是SIM卡安全体系的二级解锁机制。

### Physical Cell Identifier (PCI)；物理小区标识

LTE/NR物理层用于区分相邻小区的标识，LTE范围0~503、NR范围0~1007，由主/辅同步信号推导，是小区搜索、解调与切换的关键参数。

### PLMN Network Name (PNN)；PLMN网络名称

运营商在SIM/eUICC中维护的网络名称列表，与OPL配合根据当前驻留PLMN动态显示运营商名称。

### Profile；配置文件

eSIM体系下驻留于eUICC的一组运营商订阅数据集合（含IMSI、密钥、文件系统等），等效于一张虚拟SIM卡，同一eUICC上可多份共存但通常仅一个启用。

### Profile Policy Rule (PPR)；配置文件策略规则

由运营商下发并写入配置文件的策略，约束其禁用、删除等行为（如不可禁用、不可删除），违反时操作将被拒绝。

### Protocol Data Unit (PDU)；协议数据单元

短信/彩信在网络与终端间传输的协议层封装格式，含消息头（地址、协议标识、时间戳等）与用户数据，按消息类型区分头结构。

### Public Land Mobile Network (PLMN)；公用陆地移动网

由MCC+MNC唯一标识的移动运营商网络，是终端选网、漫游、注册的基本单位，每个PLMN对应特定运营商在特定国家的网络。

### Primary Scrambling Code (PSC)；主扰码

WCDMA中区分小区的512个扰码之一，是终端识别相邻小区、进行软切换的关键参数，与PCI在LTE中的角色类似。

## R

### Radio Access Technology (RAT)；无线接入技术

终端接入移动网络所使用的无线空口技术规范，是区分不同代际和制式网络的核心维度，如GSM、WCDMA、LTE、NR各为不同RAT。

### Removable User Identity Module (RUIM)；可移动用户身份模块

用于CDMA网络的可插拔用户识别卡，功能与GSM中的SIM对应，与USIM、ISIM等并列区分不同制式的用户身份模块。

### Replace Short Message；替换短信

3GPP TS 23.040定义的一类特殊短信，用于替换终端中先前由同一发送方存储的同标识消息，避免重复存储，与普通短信及状态报告相区分。

### Roaming；漫游

终端在非归属运营商网络上使用蜂窝数据或语音服务的状态，需运营商间协议支持并通常产生额外费用；蜂窝数据漫游需单独开关控制，与蜂窝数据总开关独立。

## S

### Service Provider Name (SPN)；服务提供商名称

存储在SIM卡EF_SPN文件中的运营商服务名，用于终端状态栏等位置显示，区别于网络名（PNN），其显示规则由SPN显示条件控制。

### SGP.22；eUICC技术规范

GSMA SGP.22规范，定义eUICC与SM-DP+之间的远程配置文件管理协议（含认证、下载、安装、策略等流程），是eSIM互操作性的国际技术基线。

### Short Message Service (SMS)；短消息业务

在移动网络上传输有限长度文本或数据消息的电信业务，俗称“短信”，通过SMSC存储转发，单条容量受编码方式约束。

### Short Message Service Center (SMSC)；短消息服务中心

移动网络中负责短信存储转发的核心网元，终端发送短信时先提交至此，由其按目标地址寻址投递。

### SIM Application Toolkit；SIM应用工具包

3GPP/ETSI定义的主动式命令机制，允许SIM卡主动与终端交互（下发菜单、刷新、呼叫控制等），终端通过信封命令上报事件、终端响应主动指令。

### SIM Authentication；SIM卡鉴权

利用SIM/eUICC内置密钥与算法在终端与网络间完成身份验证的过程，支持EAP-SIM、EAP-AKA等类型，用于WLAN/IMS等接入场景借用SIM凭证完成认证。

### Single-Carrier Radio Transmission Technology (1XRTT)；单载波无线电传输技术

CDMA20001X空口采用的无线传输技术，单载波提供话音与中低速分组数据业务，是IS-95向EVDO演进的中间代际制式，与EVDO分工承担话音与数据。

### Slot；卡槽

设备上用于插入SIM卡的物理或逻辑槽位，通过卡槽ID（slotId）区分，多卡设备中卡槽1对应ID为0、卡槽2对应ID为1，用于定位操作作用于哪张卡。

### SMS Status Report；短信状态报告

SMSC向终端返回的、告知发送方短信送达状态的特定格式短消息，与发送结果回调及送达报告回调协同构成短信发送的完整反馈链路。

### Standalone (SA)；独立组网

5G NR直接接入5GC的完整部署模式，支持网络切片、超低时延等5G全部特性，是5G的最终目标架构，与NSA相比需完整5GC部署。

### Subscriber Identity Module (SIM)；用户身份模块

3GPP体系中存储用户身份（IMSI）、鉴权密钥、电话簿等数据的可插拔智能卡，是接入移动网络的凭据载体，泛指包含USIM、ISIM、RUIM在内的所有形态。

### Subscription Manager Data Preparation Plus (SM-DP+)；订阅管理器数据准备服务器

GSMA标准定义的、负责为eUICC准备并下发配置文件的运营商侧服务器，是eSIM远程配置的核心节点。

### Synchronized Multimedia Integration Language (SMIL)；同步多媒体集成语言

基于XML的标记语言，用于描述多媒体演示中各组成部分的时间编排与布局，在彩信中作为附件控制内容播放顺序与版式。

### System Identification (SID)；系统识别码

CDMA网络中标识运营商系统的编号，与NID共同确定CDMA终端的归属网络和漫游状态。

## T

### Tag-Length-Value (TLV)；标签-长度-值

智能卡（含SIM/eUICC）数据交换中标准的编码格式，每条数据由标签、长度、值三段组成可嵌套，便于卡侧按BER-TLV规则解析。

### Terminal Response；终端响应

SIM应用工具包（USAT）中终端对SIM卡主动命令的应答数据，包含命令执行状态与可选数据回传，与信封命令共同构成ME↔UICC应用层交互闭环。

### Tianjitong；天际通

HarmonyOS设备提供的境外数据漫游服务，通过虚拟SIM卡为用户提供境外蜂窝数据接入，在默认移动数据场景下占用特殊slotId，区别于普通物理SIM卡。

### Time Division Multiplexing (TDM)；时分复用

DSDS V5_TDM模式下两卡共享同一射频通道的复用方式，通过时间片切换在两卡间交替收发，使双卡均可待机但同一时刻仅一卡可业务。

### Time Division-Synchronous Code Division Multiple Access (TD-SCDMA)；时分同步码分多址

3GPP定义的3G TDD空口标准，采用智能天线和同步CDMA技术，主要在中国部署，是中国自主提出的第三代移动通信国际标准。

### TP-Reply-Path；TP回复路径

SMS TPDU中指示回复消息是否经由原发送方所用SMSC路由的协议字段，为true时接收方回复将使用原短信的SMSC地址而非默认SMSC。

### Tracking Area Code (TAC)；跟踪区域代码

LTE/NR中标识跟踪区的编号，跟踪区是PS域移动性管理单位，替代CS域的LAC，终端跨跟踪区移动时触发跟踪区更新。

## U

### Universal Character Set 2 (UCS-2)；通用双字节字符集

短信中用于编码非GSM默认字母表字符（如中文）的16位编码方案，使用时单条SMS容量从160字符（7位）降为70字符。

### Universal Mobile Telecommunications System (UMTS)；通用移动通信系统

3GPP制定的第三代移动通信（3G）系统，其短信协议与GSM、LTE同属3GPP（“3gpp”）协议族，PDU结构与编码方式一致，与3GPP2（CDMA）短信协议相区分。

### Universal Subscriber Identity Module (USIM)；通用用户身份模块

3G/4G/5G网络使用的、兼容SIM但增强安全性的用户身份模块，支持更长密钥与双向认证，是EAP-AKA、IMS等业务的能力基础。

### User Agent (UA)；用户代理

MMS客户端在与MMSC交互时标识自身类型与能力的字符串，类似HTTP的User-Agent头，MMSC可据此返回适配的内容格式。

### User Agent Profile (UAProf)；用户代理描述

描述MMS终端硬件能力（屏幕尺寸、支持媒体类型等）的描述文件URL，MMSC据此对彩信内容进行转码适配，与UA配合使用。

### Ut；补充业务接口

基于HTTP/XCAP的补充业务（呼叫转移、呼叫等待等）配置接口，区别于传统SS信令，其连接与下发受运营商支持情况影响。

### UTRA Absolute Radio Frequency Channel Number (UARFCN)；UTRA绝对无线频率信道号

WCDMA/TD-SCDMA中标识UTRA载波频点的编号，以200kHz为单位换算绝对频率，用于3G网络频点配置与测量上报。

## V

### vCard；电子名片

表示联系人信息（姓名、电话、地址、URL、照片等）的文件格式标准，OpenHarmony中VCard模块支持将其导入联系人数据库或反向导出，支持2.1/3.0/4.0版本。

### vCard File (VCF)；vCard文件

符合vCard标准的联系人信息文件（扩展名.vcf），以纯文本键值对组织联系人字段，用于导入导出操作。

### Voice over LTE (VoLTE)；LTE语音

基于IMS架构在LTE数据承载上提供的语音业务，区别于传统CS域语音，其支持与开关受运营商配置项控制。

## W

### WAP Push；WAP推送

基于WAP协议向终端主动推送内容（URL、配置参数、彩信通知等）的机制，通常以数据短信（端口寻址）为承载；彩信流程中MMSC通过其向接收方下发通知。

### Wideband Code Division Multiple Access (WCDMA)；宽带码分多址

3GPP定义的3G FDD空口标准，使用5MHz宽带DS-CDMA接入，可同时承载CS话音与HSPA高速分组数据业务，是欧洲及全球多数运营商的3G主流制式。

## #

### 5G Core (5GC)；5G核心网

3GPP R15起定义的5G核心网，采用服务化架构并支持网络切片与控制面/用户面分离，与NG-RAN配合构成SA组网，是5G完整能力的基础，区别于4G EPC核心网。