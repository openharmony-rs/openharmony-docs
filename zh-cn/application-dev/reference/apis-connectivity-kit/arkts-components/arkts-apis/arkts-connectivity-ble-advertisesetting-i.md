# AdvertiseSetting

描述BLE广播的发送参数。

**起始版本：** 10

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## 导入模块

```TypeScript
import { ble } from '@kit.ConnectivityKit';
```

## connectable

```TypeScript
connectable?: boolean
```

是否是可连接广播。true表示发送可连接广播，false表示发送不可连接广播，默认值为true。

**类型：** boolean

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## interval

```TypeScript
interval?: number
```

广播发送间隔。

取值范围：[32, 16777215]，单位：slot（时间槽），一个slot代表0.625毫秒，默认值为1600。

其中传统广播的最大值是16384。

**类型：** number

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## isExtended

```TypeScript
isExtended?: boolean
```

是否使用扩展广播。false表示使用传统广播，报文最大长度为31个字节；true表示使用扩展广播，报文最大长度由蓝牙芯片能力决定。默认值为false。

**起始版本**：26.0.0

**类型：** boolean

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## txPower

```TypeScript
txPower?: number
```

广播发送功率。取值范围：[-127, 1]，单位：dBm，默认值为-7。

考虑到发送广播的性能和功耗，建议高档取值为1，中档取为-7，低档取值为-15。

**类型：** number

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core
