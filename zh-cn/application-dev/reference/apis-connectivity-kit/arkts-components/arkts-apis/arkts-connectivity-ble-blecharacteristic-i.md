# BLECharacteristic

GATT特征值结构定义，是服务[GattService](arkts-connectivity-ble-gattservice-i.md)的核心数据单元。

**起始版本：** 10

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## 导入模块

```TypeScript
import { ble } from '@kit.ConnectivityKit';
```

## characteristicUuid

```TypeScript
characteristicUuid: string
```

特征值UUID。例如：00002a11-0000-1000-8000-00805f9b34fb。

**类型：** string

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## characteristicValue

```TypeScript
characteristicValue: ArrayBuffer
```

特征值的数据内容。

**类型：** ArrayBuffer

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## characteristicValueHandle

```TypeScript
characteristicValueHandle?: number
```

特征值的唯一标识句柄。当server端BLE蓝牙设备提供了多个相同UUID特征值时，可以通过此句柄区分不同的特征值。若不设置此参数，则内容为undefined。

**类型：** number

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## descriptors

```TypeScript
descriptors: Array<BLEDescriptor>
```

特征值包含的描述符列表。

**类型：** Array&lt;[BLEDescriptor](arkts-connectivity-ble-bledescriptor-i.md)&gt;

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## permissions

```TypeScript
permissions?: GattPermissions
```

特征值读写操作需要的权限。若不设置此参数，则使用默认权限值。

**类型：** [GattPermissions](arkts-connectivity-ble-gattpermissions-i.md)

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## properties

```TypeScript
properties?: GattProperties
```

特征值支持的属性。若不设置此参数，则使用默认属性值。

**类型：** [GattProperties](arkts-connectivity-ble-gattproperties-i.md)

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## serviceUuid

```TypeScript
serviceUuid: string
```

特征值所属的服务UUID。例如：00001888-0000-1000-8000-00805f9b34fb。

**类型：** string

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core
