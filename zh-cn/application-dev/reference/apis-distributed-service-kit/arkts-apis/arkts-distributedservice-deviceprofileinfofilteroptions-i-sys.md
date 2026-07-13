# DeviceProfileInfoFilterOptions（系统接口）

设备信息过滤器选项。

**起始版本：** 15

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

## deviceIdList

```TypeScript
deviceIdList?: Array<string>
```

表示获取指定deviceId的设备信息，deviceId一般为设备的UDID，如设备无UDID，则取其MAC或SN作为deviceId。默认为空。

**类型：** Array<string>

**起始版本：** 15

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

## isCloud

```TypeScript
isCloud : boolean
```

表示是否需要实时从云端获取设备列表。

- false：表示从设备获取。
- true：表示从云端获取。

**类型：** boolean

**起始版本：** 15

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

