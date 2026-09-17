# PhyValue

连接链路的物理通道类型配置参数。

**起始版本：** 23

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## 导入模块

```TypeScript
import { ble } from '@kit.ConnectivityKit';
```

## phyMode

```TypeScript
phyMode?: CodedPhyMode
```

用于指定物理通道类型为[BLE_PHY_CODED](arkts-connectivity-ble-blephy-e.md)的编码方式。

默认值为0，表示不指定明确的编码方式，由蓝牙子系统决定。

**类型：** [CodedPhyMode](arkts-connectivity-ble-codedphymode-e.md)

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## rxPhy

```TypeScript
rxPhy: BlePhy
```

接收端物理通道类型。

**类型：** [BlePhy](arkts-connectivity-ble-blephy-e.md)

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## txPhy

```TypeScript
txPhy: BlePhy
```

发送端物理通道类型。

**类型：** [BlePhy](arkts-connectivity-ble-blephy-e.md)

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core
