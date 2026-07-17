# FeatureForDevice

设备特性枚举。

**起始版本：** 24

<!--Device-restrictions-enum FeatureForDevice--><!--Device-restrictions-enum FeatureForDevice-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## WIFI_P2P

```TypeScript
WIFI_P2P = 0
```

Wi-Fi P2P（点对点连接），允许设备在没有接入点的情况下直接相互连接。禁用后，设备无法通过Wi-Fi P2P进行点对点连接，影响文件传输、游戏联机、屏幕共享等需要直接Wi-Fi连接的应用功能。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FeatureForDevice-WIFI_P2P = 0--><!--Device-FeatureForDevice-WIFI_P2P = 0-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## LOCAL_INPUT

```TypeScript
LOCAL_INPUT = 2
```

本地输入（包含键盘、鼠标、触控板、触摸屏等）被禁用后，无法通过本地输入进行操作。重启设备可解除禁用。在息屏状态下禁用会导致屏幕无法唤醒，若禁用后屏幕自动息屏，同样会导致无法唤醒屏幕。

26.0.0

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FeatureForDevice-LOCAL_INPUT = 2--><!--Device-FeatureForDevice-LOCAL_INPUT = 2-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## SUDO

```TypeScript
SUDO = 4
```

超级用户执行

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FeatureForDevice-SUDO = 4--><!--Device-FeatureForDevice-SUDO = 4-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## TRAFFIC_REDIRECTION

```TypeScript
TRAFFIC_REDIRECTION = 5
```

流量重定向

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FeatureForDevice-TRAFFIC_REDIRECTION = 5--><!--Device-FeatureForDevice-TRAFFIC_REDIRECTION = 5-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## CORE_DUMP

```TypeScript
CORE_DUMP = 6
```

创建文件转储。禁用后，无法通过任务管理器创建文件转储。

26.0.0

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FeatureForDevice-CORE_DUMP = 6--><!--Device-FeatureForDevice-CORE_DUMP = 6-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## RS232

```TypeScript
RS232 = 7
```

RS232串口

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FeatureForDevice-RS232 = 7--><!--Device-FeatureForDevice-RS232 = 7-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## DISK_ERASURE

```TypeScript
DISK_ERASURE = 8
```

安全擦除

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FeatureForDevice-DISK_ERASURE = 8--><!--Device-FeatureForDevice-DISK_ERASURE = 8-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## MODIFY_DATE_TIME

```TypeScript
MODIFY_DATE_TIME = 10
```

安全擦除

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FeatureForDevice-MODIFY_DATE_TIME = 10--><!--Device-FeatureForDevice-MODIFY_DATE_TIME = 10-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

