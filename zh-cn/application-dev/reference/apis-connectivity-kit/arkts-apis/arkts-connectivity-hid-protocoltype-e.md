# ProtocolType

枚举，HID设备与主机的通信协议类型。

**起始版本：** 23

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## PROTOCOL_BOOT_MODE

```TypeScript
PROTOCOL_BOOT_MODE = 0
```

兼容模式，确保设备在系统启动阶段和所有平台都能被识别为基本输入设备，兼容性最好但功能有限，适用于如键盘鼠标简单外设开发。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## PROTOCOL_REPORT_MODE

```TypeScript
PROTOCOL_REPORT_MODE = 1
```

完整的报告协议模式，允许设备使用完整的HID描述符和所有报告类型，适用于如游戏手柄、触摸屏等需要丰富功能与自定义数据格式的复杂外设。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core
