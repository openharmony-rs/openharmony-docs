# BundleUsedRecord（系统接口）

某个应用或设备的访问记录。

**起始版本：** 9

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

## bundleName

```TypeScript
bundleName: string
```

使用权限的应用包名。在本端场景下可用于直接定位目标应用；分布式场景下该字段无效。

**类型：** string

**起始版本：** 9

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

## deviceId

```TypeScript
deviceId: string
```

使用权限的应用所在设备ID。主要在分布式场景下用于识别远端设备来源；本端场景下通常可忽略该字段。

**类型：** string

**起始版本：** 9

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

## deviceName

```TypeScript
deviceName?: string
```

使用权限的应用所在设备名称，仅用于分布式场景。可用于在界面中展示更易理解的设备标识。
默认值：空字符串。

**类型：** string

**起始版本：** 24

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

## isRemote

```TypeScript
isRemote: boolean
```

是否是分布式场景的访问记录。false表示本端应用记录，true表示远端设备上的权限使用记录。

**类型：** boolean

**起始版本：** 9

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

## permissionRecords

```TypeScript
permissionRecords: Array<PermissionUsedRecord>
```

当前应用或设备下的权限使用记录集合。每个元素对应一个具体权限，可进一步查看访问次数、拒绝次数、最后访问时间及明细记录。

**类型：** Array<PermissionUsedRecord>

**起始版本：** 9

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

## tokenId

```TypeScript
tokenId: number
```

使用权限的应用身份标识。分布式场景下该字段无效，需结合deviceId和deviceName识别来源设备。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

