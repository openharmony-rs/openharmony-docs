# CodedPhyMode

枚举，BLE_PHY_CODED类型下的编码方式。

**起始版本：** 23

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## BLE_PHY_CODED_S2

```TypeScript
BLE_PHY_CODED_S2 = 1
```

每发送1位有效数据，会添加1位冗余信息。传输速度较快，抗干扰较强，适合中等距离（10 - 100m），理论数据速率为500Kbit/s。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## BLE_PHY_CODED_S8

```TypeScript
BLE_PHY_CODED_S8 = 2
```

每发送1位有效数据，会添加7位冗余信息。传输速度较慢，抗干扰更强，适合远距离（100 - 300m），理论数据速率为125Kbit/s。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core
