# ServiceInfo（系统接口）

云服务信息

**起始版本：** 11

**ArkTS模式：** ArkTS-Dyn起始版本为11；ArkTS-Sta起始版本为23。

<!--Device-cloudExtension-export interface ServiceInfo--><!--Device-cloudExtension-export interface ServiceInfo-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Server

**系统接口：** 此接口为系统接口。

## enableCloud

```TypeScript
enableCloud: boolean
```

表示是否启用了云服务。true表示启用云服务，false表示未启用

**类型：** boolean

**起始版本：** 11

**ArkTS模式：** ArkTS-Dyn起始版本为11；ArkTS-Sta起始版本为23。

<!--Device-ServiceInfo-enableCloud: boolean--><!--Device-ServiceInfo-enableCloud: boolean-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Server

**系统接口：** 此接口为系统接口。

## id

```TypeScript
id: string
```

使用哈希函数SHA256生成的云账号ID。

**类型：** string

**起始版本：** 11

**ArkTS模式：** ArkTS-Dyn起始版本为11；ArkTS-Sta起始版本为23。

<!--Device-ServiceInfo-id: string--><!--Device-ServiceInfo-id: string-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Server

**系统接口：** 此接口为系统接口。

## remainingSpace

```TypeScript
remainingSpace: long
```

服务器上账号的可用空间（KB）。

**类型：** long

**起始版本：** 11

**ArkTS模式：** ArkTS-Dyn起始版本为11；ArkTS-Sta起始版本为23。

<!--Device-ServiceInfo-remainingSpace: long--><!--Device-ServiceInfo-remainingSpace: long-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Server

**系统接口：** 此接口为系统接口。

## totalSpace

```TypeScript
totalSpace: long
```

服务器上账号的总空间（KB）。

**类型：** long

**起始版本：** 11

**ArkTS模式：** ArkTS-Dyn起始版本为11；ArkTS-Sta起始版本为23。

<!--Device-ServiceInfo-totalSpace: long--><!--Device-ServiceInfo-totalSpace: long-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Server

**系统接口：** 此接口为系统接口。

## user

```TypeScript
user: int
```

设备的当前用户ID。

**类型：** int

**起始版本：** 11

**ArkTS模式：** ArkTS-Dyn起始版本为11；ArkTS-Sta起始版本为23。

<!--Device-ServiceInfo-user: int--><!--Device-ServiceInfo-user: int-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Server

**系统接口：** 此接口为系统接口。

