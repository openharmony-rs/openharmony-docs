# ErrorReason

枚举，描述错误原因。

**起始版本：** 23

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## RSP_SUCCESS

```TypeScript
RSP_SUCCESS = 0
```

成功无异常。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## RSP_NOT_READY

```TypeScript
RSP_NOT_READY = 1
```

设备未准备好处理请求。建议主机稍后重试。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## RSP_INVALID_REPORT_ID

```TypeScript
RSP_INVALID_REPORT_ID = 2
```

无效的报告ID。建议主机确认当前支持的ID列表，并使用正确的ID重发消息。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## RSP_UNSUPPORTED_REQ

```TypeScript
RSP_UNSUPPORTED_REQ = 3
```

当前请求不支持，建议主机检查当前请求类型或报告类型是否在当前协议模式下被本端支持。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## RSP_INVALID_PARAM

```TypeScript
RSP_INVALID_PARAM = 4
```

无效参数。建议主机检查请求中的参数是否超出本端声明的范围或不符合报告描述符的定义。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## RSP_UNKNOWN

```TypeScript
RSP_UNKNOWN = 14
```

未知错误原因。建议主机记录错误上下文并重试。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core
