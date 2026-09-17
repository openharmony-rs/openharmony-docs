# UnbondCause

枚举，配对失败原因。

**起始版本：** 12

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## USER_REMOVED

```TypeScript
USER_REMOVED = 0
```

用户主动移除设备。若配对状态[BondState](arkts-connectivity-connection-bondstate-e.md)是已配对，也表示配对成功。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## REMOTE_DEVICE_DOWN

```TypeScript
REMOTE_DEVICE_DOWN = 1
```

对端设备不在线。例如：对端设备蓝牙是关闭的。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## AUTH_FAILURE

```TypeScript
AUTH_FAILURE = 2
```

鉴权失败。例如：两端设备密钥不匹配。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## AUTH_REJECTED

```TypeScript
AUTH_REJECTED = 3
```

鉴权被拒绝。例如：对端设备拒绝了配对请求。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## INTERNAL_ERROR

```TypeScript
INTERNAL_ERROR = 4
```

内部错误。例如：设备不支持配对、配对过程超时等异常。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core
