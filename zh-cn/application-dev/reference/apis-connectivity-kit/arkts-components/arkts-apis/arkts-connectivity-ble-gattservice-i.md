# GattService

GATT服务结构定义，可包含多个特征值[BLECharacteristic](arkts-connectivity-ble-blecharacteristic-i.md)和依赖的其他服务。

**起始版本：** 10

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## 导入模块

```TypeScript
import { ble } from '@kit.ConnectivityKit';
```

## characteristics

```TypeScript
characteristics: Array<BLECharacteristic>
```

当前服务包含的特征值列表。

**类型：** Array&lt;[BLECharacteristic](arkts-connectivity-ble-blecharacteristic-i.md)&gt;

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## includeServices

```TypeScript
includeServices?: Array<GattService>
```

当前服务依赖的其它服务。若不设置此参数，则默认不依赖其它服务。

**类型：** Array&lt;[GattService](arkts-connectivity-ble-gattservice-i.md)&gt;

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## isPrimary

```TypeScript
isPrimary: boolean
```

是否是主服务。true表示是主服务，false表示是次要服务。

**类型：** boolean

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## serviceUuid

```TypeScript
serviceUuid: string
```

服务UUID，标识一个GATT服务。例如：00001888-0000-1000-8000-00805f9b34fb。

**类型：** string

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core
