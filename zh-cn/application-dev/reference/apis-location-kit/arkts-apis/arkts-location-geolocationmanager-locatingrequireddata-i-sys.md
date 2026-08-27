# LocatingRequiredData（系统接口）

表示定位业务所需的数据，包含WiFi或蓝牙扫描结果，APP拿到这些数据之后可以用于网络定位等业务。

**起始版本：** 10

**系统能力：** SystemCapability.Location.Location.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
```

## bluetoothData

```TypeScript
bluetoothData?: BluetoothScanInfo
```

表示蓝牙扫描结果。

**类型：** [BluetoothScanInfo](arkts-location-geolocationmanager-bluetoothscaninfo-i-sys.md)

**起始版本：** 10

**系统能力：** SystemCapability.Location.Location.Core

**系统接口：** 此接口为系统接口。

## campedCellInfo

```TypeScript
campedCellInfo?: CellInfo
```

表示驻留小区信息。

**类型：** [CellInfo](arkts-location-geolocationmanager-cellinfo-i-sys.md)

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Location.Location.Core

**系统接口：** 此接口为系统接口。

## neighboringCellInfo

```TypeScript
neighboringCellInfo?: CellInfo[]
```

表示邻区信息。

**类型：** [CellInfo](arkts-location-geolocationmanager-cellinfo-i-sys.md)[]

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Location.Location.Core

**系统接口：** 此接口为系统接口。

## slotId

```TypeScript
slotId?: number
```

表示SIM卡的卡槽号。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Location.Location.Core

**系统接口：** 此接口为系统接口。

## wifiData

```TypeScript
wifiData?: WifiScanInfo
```

表示WiFi扫描结果。

**类型：** WifiScanInfo

**起始版本：** 10

**系统能力：** SystemCapability.Location.Location.Core

**系统接口：** 此接口为系统接口。
