# PartnerAgentExtensionAbilityDestroyReason

枚举，PartnerAgentExtensionAbility被销毁的原因。

**起始版本：** 23

**系统能力：** SystemCapability.Communication.FusionConnectivity.Core

## UNKNOWN_REASON

```TypeScript
UNKNOWN_REASON = 0
```

系统内部导致的未知原因，建议重试该操作。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.FusionConnectivity.Core

## USER_CLOSED_ABILITY

```TypeScript
USER_CLOSED_ABILITY = 1
```

用户在系统设置应用中关闭了该设备的信息互通功能，建议在系统设置应用中开启该设备的信息互通功能。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.FusionConnectivity.Core

## DEVICE_UNPAIRED

```TypeScript
DEVICE_UNPAIRED = 2
```

用户取消了该设备的蓝牙配对关系，建议重新进行蓝牙配对流程。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.FusionConnectivity.Core

## DEVICE_LOST

```TypeScript
DEVICE_LOST = 3
```

该设备已断开连接或未被发现，可能原因包括距离过长、设备关机、设备电量耗尽等，建议确认设备状态

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.FusionConnectivity.Core

## BLUETOOTH_DISABLED

```TypeScript
BLUETOOTH_DISABLED = 4
```

蓝牙被关闭，建议打开蓝牙

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.FusionConnectivity.Core
