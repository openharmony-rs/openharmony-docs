# FeatureForDevice

设备特性枚举。

**起始版本：** 24

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## WIFI_P2P

```TypeScript
WIFI_P2P = 0
```

Wi-Fi P2P（点对点连接），允许设备在没有接入点的情况下直接相互连接。禁用后，设备无法通过Wi-Fi P2P进行点对点连接，影响文件传输、游戏联机、屏幕共享等需要直接Wi-Fi连接的应用功能。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## X_KEY

```TypeScript
X_KEY = 1
```

x键

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## LOCAL_INPUT

```TypeScript
LOCAL_INPUT = 2
```

本地输入（包含键盘、鼠标、触控板、触摸屏等）被禁用后，无法通过本地输入进行操作。重启设备可解除禁用。在息屏状态下禁用会导致屏幕无法唤醒，若禁用后屏幕自动息屏，同样会导致无法唤醒屏幕。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## PACKET_FILTERING

```TypeScript
PACKET_FILTERING = 3
```

网络包过滤

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## SUDO

```TypeScript
SUDO = 4
```

超级用户执行

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## TRAFFIC_REDIRECTION

```TypeScript
TRAFFIC_REDIRECTION = 5
```

网络流量重定向管控策略。禁用后，无法将TCP流量重定向到其它端口，取消禁用之后可恢复使用。当前仅支持PC/2in1设备使用。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## CORE_DUMP

```TypeScript
CORE_DUMP = 6
```

创建文件转储。禁用后，无法通过任务管理器创建文件转储。当前仅支持PC/2in1设备使用。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## RS232

```TypeScript
RS232 = 7
```

RS-232串口管控策略。禁用后，无法通过RS-232串口传输数据。当前仅支持PC/2in1设备使用（部分设备不支持RS-232串口）。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## DISK_ERASURE

```TypeScript
DISK_ERASURE = 8
```

磁盘擦除能力。禁用后，"磁盘擦除"入口将被置灰。当前仅支持PC/2in1设备使用。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## BLUETOOTH

```TypeScript
BLUETOOTH = 9
```

设备蓝牙能力。当已经通过 [addDisallowedBluetoothDevices](arkts-mdm-bluetoothmanager-adddisallowedbluetoothdevices-f.md) 接口或者 [addAllowedBluetoothDevices](arkts-mdm-bluetoothmanager-addallowedbluetoothdevices-f.md) 接口设置了蓝牙设备禁用名单或者允许名单，再禁用设备蓝牙能力，会优先生效禁用设备蓝牙能力。直到设备蓝牙能力启用后，禁止或允许名单才会生效。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## MODIFY_DATE_TIME

```TypeScript
MODIFY_DATE_TIME = 10
```

设备修改系统时间能力。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## PRINTER

```TypeScript
PRINTER = 11
```

设备打印能力。禁用了设备打印能力时，通过[setDisallowedPolicyForAccount](arkts-mdm-restrictions-setdisallowedpolicyforaccount-f.md)接口开启某用户的打印能 力，该用户下的打印能力仍然被禁用。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## HDC

```TypeScript
HDC = 12
```

被其他设备通过hdc连接、调试的能力。设置禁用后，其他设备无法通过hdc连接、调试此设备。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## MICROPHONE

```TypeScript
MICROPHONE = 13
```

设备麦克风能力。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## FINGERPRINT

```TypeScript
FINGERPRINT = 14
```

设备指纹认证能力。当已经通过[setDisallowedPolicyForAccount](arkts-mdm-restrictions-setdisallowedpolicyforaccount-f.md)设置了某用户禁用设备指纹认证能力时， 再启用设备指纹认证能力，会报策略冲突。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## USB

```TypeScript
USB = 15
```

设备USB能力。禁用后外接的USB设备无法使用，即在当前设备为HOST模式时，无法外接其他DEVICE设备。以下五种情况再禁用设备USB能力，会报策略冲突。1）通过[addAllowedUsbDevices](arkts-mdm-usbmanager-addallowedusbdevices-f.md)接口添加了USB设备可用名单。2）通过[setUsbStorageDeviceAccessPolicy](arkts-mdm-usbmanager-setusbstoragedeviceaccesspolicy-f.md)接口 设置了USB存储设备访问策略为只读/禁用。3）通过[addDisallowedUsbDevices](arkts-mdm-usbmanager-adddisallowedusbdevices-f.md)接口添加了禁止使用的USB设 备类型。4）通过[setDisallowedPolicyForAccount](arkts-mdm-restrictions-setdisallowedpolicyforaccount-f.md)接口禁用了某用户USB存储设备写入能力。5）禁用USB转串口（[USB_SERIAL](#featurefordevice)）。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## WIFI

```TypeScript
WIFI = 16
```

设备Wi-Fi能力。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## TETHERING

```TypeScript
TETHERING = 17
```

网络共享能力（设备已有网络共享给其他设备的能力，即共享热点能力）。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## INACTIVE_USER_FREEZE

```TypeScript
INACTIVE_USER_FREEZE = 18
```

非活跃用户运行能力。禁用后，非UIAbility进程一般不会被冻结，UIAbility申请短时任务、长时任务、延迟任务或能效资源等后台运行任务也不会被冻结。当前仅支持PC/2in1设备使用。企业空间场景下，系统切换到企业空间用 户，个人空间用户属于非活跃用户。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## CAMERA

```TypeScript
CAMERA = 19
```

设备相机能力。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## MTP_CLIENT

```TypeScript
MTP_CLIENT = 20
```

MTP客户端能力（包含读取和写入），当前仅支持PC/2in1设备使用。MTP（MediaTransferProtocol，媒体传输协议），该协议允许用户在移动设备上线性访问媒体文件。当已经通过 [setDisallowedPolicyForAccount](arkts-mdm-restrictions-setdisallowedpolicyforaccount-f.md)设置了某用户禁用MTP客户端写入能力时，再禁用MTP客户端能力， 会报策略冲突。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## MTP_SERVER

```TypeScript
MTP_SERVER = 21
```

MTP服务端能力，当前仅支持手机、平板设备使用。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## SAMBA_CLIENT

```TypeScript
SAMBA_CLIENT = 22
```

samba客户端能力，当前仅支持PC/2in1设备使用。samba是在Linux和UNIX系统上实现SMB协议的一个免费软件，由服务器及客户端程序构成。SMB（Server Message Block，信息服务块）是一种在局域 网上共享文件和打印机的一种通信协议，它为局域网内的不同计算机之间提供文件及打印机等资源的共享服务。SMB协议是客户机/服务器型协议，客户机通过该协议可以访问服务器上的共享文件系统、打印机及其他资源。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## SAMBA_SERVER

```TypeScript
SAMBA_SERVER = 23
```

samba服务端能力，当前仅支持PC/2in1设备使用。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## BACKUP_AND_RESTORE

```TypeScript
BACKUP_AND_RESTORE = 24
```

备份和恢复能力，禁用后设备的"设置--系统--备份和恢复"、"设置--云空间"置灰，当前仅支持手机、平板使用。如果要完全禁用设备的备份和恢复能力，建议同时调用 [applicationManager.addDisallowedRunningBundlesSync](arkts-mdm-applicationmanager-adddisallowedrunningbundlessync-f.md) 接口禁止具备备份和恢复能力的应用运行，如备份和恢复、手机助手、云空间应用。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## MAINTENANCE_MODE

```TypeScript
MAINTENANCE_MODE = 25
```

设备维修模式能力。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## MMS

```TypeScript
MMS = 26
```

multimedia messaging service，设备接收、发送彩信的能力，当前仅支持手机、平板设备使用。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## SMS

```TypeScript
SMS = 27
```

short messaging service，设备接收、发送短信的能力，当前仅支持手机、平板设备使用。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## MOBILE_DATA

```TypeScript
MOBILE_DATA = 28
```

蜂窝数据能力，当前仅支持手机、平板设备使用。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## AIRPLANE_MODE

```TypeScript
AIRPLANE_MODE = 29
```

飞行模式能力，当前仅支持手机、平板设备使用。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## VPN

```TypeScript
VPN = 30
```

Virtual Private Network（虚拟专用网络），VPN能力。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## NOTIFICATION

```TypeScript
NOTIFICATION = 31
```

设备通知能力。禁用后，由系统应用和第三方应用发出的通知将不会显示，而系统服务通知能力不受影响。当此设备已经通过 [addAllowedNotificationBundles](arkts-mdm-applicationmanager-addallowednotificationbundles-f.md) 设置了应用通知允许名单之后，再禁用设备通知能力，会抛出错误码9200010。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## NFC

```TypeScript
NFC = 32
```

Near Field Communication（近距离无线通信），NFC能力，当前仅支持手机、平板设备使用。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## PRIVATE_SPACE

```TypeScript
PRIVATE_SPACE = 33
```

创建隐私空间能力，当前仅支持手机、平板使用。对已创建的隐私空间无效。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## TELEPHONE_CALL

```TypeScript
TELEPHONE_CALL = 34
```

设备通话能力，禁用后电话无法呼入和呼出。当前仅支持手机、平板设备使用。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## APP_CLONE

```TypeScript
APP_CLONE = 35
```

[应用分身能力](../../../quick-start/app-clone.md)，禁用后无法创建应用分身。对已创建的应用分身无效。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## EXTERNAL_STORAGE_CARD

```TypeScript
EXTERNAL_STORAGE_CARD = 36
```

外置存储能力，禁用后设备无法使用外置存储，并且当前已连接的外置存储会被卸载。如果外置存储卸载时有文件正在被使用，可能会导致卸载失败，返回9200013错误码。外置存储禁用后重新启用，需要手动重新连接外置存储。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## RANDOM_MAC

```TypeScript
RANDOM_MAC = 37
```

Wi-Fi连接时使用随机MAC能力，设置禁用后，连接Wi-Fi仅能使用设备物理MAC。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## UNMUTE_DEVICE

```TypeScript
UNMUTE_DEVICE = 38
```

设备媒体播放声音能力，设置禁用后，设备媒体播放将静音，[蜂窝通话](../../../media/audio/audio-call-overview.md)能力不受影响。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## HDC_REMOTE

```TypeScript
HDC_REMOTE = 39
```

设备通过hdc调试其他设备的能力，当前仅支持PC/2in1设备设置。设置禁用后，无法通过hdc调试手机、平板、PC、智能手表等设备。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## VIRTUAL_SERVICE

```TypeScript
VIRTUAL_SERVICE = 40
```

设备虚拟化服务能力，即利用硬件资源的冗余，以虚拟化方式运行其他平台（如Linux、Windows）的能力。设置禁用设备虚拟化服务能力时，建议同时卸载与虚拟化服务相关的应用，并禁止其再次安装。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## USB_SERIAL

```TypeScript
USB_SERIAL = 41
```

设备USB转串口能力。禁用后外接的USB转串口设备无法使用。以下两种情况再禁用设备USB转串口能力，会报策略冲突。1）通过[addAllowedUsbDevices](arkts-mdm-usbmanager-addallowedusbdevices-f.md)接口添加了USB设备可用名单。2）禁用设备USB能力（[USB](#featurefordevice)）。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## SCREEN_SHOT

```TypeScript
SCREEN_SHOT = 42
```

截屏能力，禁用后无法进行截屏操作。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## SCREEN_RECORD

```TypeScript
SCREEN_RECORD = 43
```

录屏能力，禁用后无法进行录屏操作。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## DISK_RECOVERY_KEY

```TypeScript
DISK_RECOVERY_KEY = 44
```

恢复[密钥导出](../../../security/UniversalKeystoreKit/huks-export-key-arkts.md)能力，当前仅支持PC/2in1设备使用。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## NEAR_LINK

```TypeScript
NEAR_LINK = 45
```

星闪（NearLink）能力。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## DEVELOPER_MODE

```TypeScript
DEVELOPER_MODE = 46
```

开发者模式，禁用后设备重启生效。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## RESET_FACTORY

```TypeScript
RESET_FACTORY = 47
```

恢复出厂设置能力。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## REMOTE_DESK

```TypeScript
REMOTE_DESK = 48
```

远程桌面能力。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## REMOTE_DIAGNOSIS

```TypeScript
REMOTE_DIAGNOSIS = 49
```

远程诊断能力。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## OTA_UPDATE

```TypeScript
OTA_UPDATE = 50
```

公网系统升级能力。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager
