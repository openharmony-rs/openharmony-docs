# BeaconManufactureData

beacon设备制造商数据。

**起始版本：** 20

**系统能力：** SystemCapability.Location.Location.Geofence

## 导入模块

```TypeScript
```

## manufactureData

```TypeScript
manufactureData: ArrayBuffer
```

厂商自定义数据。例如：[0x02,0x15,0x00...0xFF,0x11,0x22,0x33,0x44,0x55]

**类型：** ArrayBuffer

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Location.Location.Geofence

## manufactureDataMask

```TypeScript
manufactureDataMask: ArrayBuffer
```

搭配manufactureData使用，可设置过滤部分制造商数据，0xFF为全匹配，0x00为模糊匹配。例如：[0xFF,0xFF,0xFF...0xFF,0xFF,0xFF,0xFF,0xFF,0xFF]

**类型：** ArrayBuffer

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Location.Location.Geofence

## manufactureId

```TypeScript
manufactureId: number
```

制造商标识。

**类型：** number

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Location.Location.Geofence
