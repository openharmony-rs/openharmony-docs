# SaveSuccessResponse

[save](arkts-arkdata-dataobject-i.md#save-1)
接口回调信息。

**起始版本：** 9

**系统能力：** SystemCapability.DistributedDataManager.DataObject.DistributedObject

## deviceId

```TypeScript
deviceId: string
```

存储数据的设备号，标识需要保存对象的设备。"local"表示本地设备，否则表示其他设备的设备号。

**类型：** string

**起始版本：** 9

**系统能力：** SystemCapability.DistributedDataManager.DataObject.DistributedObject

## sessionId

```TypeScript
sessionId: string
```

多设备协同的唯一标识。

**类型：** string

**起始版本：** 9

**系统能力：** SystemCapability.DistributedDataManager.DataObject.DistributedObject

## version

```TypeScript
version: number
```

已保存对象的版本，取值为非负整数。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.DistributedDataManager.DataObject.DistributedObject

