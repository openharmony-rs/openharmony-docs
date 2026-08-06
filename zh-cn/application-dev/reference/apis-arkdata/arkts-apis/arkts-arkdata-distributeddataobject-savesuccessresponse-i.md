# SaveSuccessResponse

[save]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_ 接口回调信息。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-distributedDataObject-interface SaveSuccessResponse--><!--Device-distributedDataObject-interface SaveSuccessResponse-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataObject.DistributedObject

## deviceId

```TypeScript
deviceId: string
```

存储数据的设备号，标识需要保存对象的设备。"local"表示本地设备，否则表示其他设备的设备号。

**类型：** string

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-SaveSuccessResponse-deviceId: string--><!--Device-SaveSuccessResponse-deviceId: string-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataObject.DistributedObject

## sessionId

```TypeScript
sessionId: string
```

多设备协同的唯一标识。

**类型：** string

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-SaveSuccessResponse-sessionId: string--><!--Device-SaveSuccessResponse-sessionId: string-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataObject.DistributedObject

## version

```TypeScript
version: int
```

已保存对象的版本，取值为非负整数。

**类型：** int

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-SaveSuccessResponse-version: int--><!--Device-SaveSuccessResponse-version: int-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataObject.DistributedObject

