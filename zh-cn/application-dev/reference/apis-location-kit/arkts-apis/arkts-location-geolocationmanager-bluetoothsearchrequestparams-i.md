# BluetoothSearchRequestParams

蓝牙扫描请求参数。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Location.Location.Core

## 导入模块

```TypeScript
```

## deviceIdArray

```TypeScript
deviceIdArray: Array<string>
```

表示蓝牙设备的地址列表，用于过滤扫描结果。单个字符串的长度不超过64，数组的长度不超过1000。仅当扫描到的蓝牙设备的地址与该数组中的一个元素相同时才通过callback返回该蓝牙设备信息。当传入空数组（数组长度为0）时，不会 返回蓝牙扫描结果。数组中每个元素的格式如下："XX:XX:XX:XX:XX:XX"。

**类型：** Array&lt;string&gt;

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Location.Location.Core

## rssiThreshold

```TypeScript
rssiThreshold?: number
```

表示RSSI阈值，只扫描RSSI大于此阈值的设备。取值范围为-128至127。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Location.Location.Core
