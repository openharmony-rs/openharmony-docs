# Telephony Kit术语
<!--Kit: Telephony Kit-->
<!--Subsystem: Telephony-->
<!--Owner: @shao-yikai-->
<!--Designer: @wnazgul-->
<!--Tester: @jiang_99-->
<!--Adviser: @zhang_yixin13-->

## A

### Access Point Name (APN)；接入点名称

移动通信中标识分组数据网络接入点的字符串，终端建立蜂窝数据连接时必须配置，决定设备经哪个网关接入运营商网络或专网。

## C

### Call Transfer；呼叫转移

电话系统中将来电按预设条件自动转接至另一号码的功能，分无条件转移、忙线转移、无回复转移、无法访问转移四种类型，用于用户无法接听时将来电转至其他号码。

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

## M

### Multimedia Messaging Service (MMS)；彩信

在移动网络上传输包含文本、图片、音频、视频等多媒体内容消息的业务，与纯文本SMS不同，采用基于WAP/HTTP的PDU封装并经MMSC存储转发。

## V

### vCard；电子名片

表示联系人信息（姓名、电话、地址、URL、照片等）的文件格式标准，OpenHarmony中VCard模块支持将其导入联系人数据库或反向导出。

### vCard File (VCF)；vCard文件

符合vCard标准的联系人信息文件（扩展名.vcf），以纯文本键值对组织联系人字段，用于导入导出操作。

### Voice over LTE (VoLTE)；LTE语音

基于IMS架构在LTE数据承载上提供的语音业务，区别于传统CS域语音，其支持与开关受运营商配置项控制。

## W

### WAP Push；WAP推送

基于WAP协议向终端主动推送内容（URL、配置参数、彩信通知等）的机制，通常以数据短信（端口寻址）为承载；彩信流程中MMSC通过其向接收方下发通知。

### Wideband Code Division Multiple Access (WCDMA)；宽带码分多址

3GPP定义的3G FDD空口标准，使用5MHz宽带DS-CDMA接入，可同时承载CS话音与HSPA高速分组数据业务，是欧洲及全球多数运营商的3G主流制式。