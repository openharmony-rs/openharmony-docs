# Volume（系统接口）

获取所有卷。

**起始版本：** 9

**系统能力：** SystemCapability.FileManagement.StorageService.Volume

**系统接口：** 此接口为系统接口。

## description

```TypeScript
description: string
```

卷设备描述。

**类型：** string

**起始版本：** 9

**系统能力：** SystemCapability.FileManagement.StorageService.Volume

**系统接口：** 此接口为系统接口。

## diskId

```TypeScript
diskId: string
```

卷设备所属的磁盘ID，一个磁盘可以有一个或者多个卷设备。磁盘设备ID的格式为disk-{主设备号}-{次设备号}，与卷设备ID相似。

**类型：** string

**起始版本：** 9

**系统能力：** SystemCapability.FileManagement.StorageService.Volume

**系统接口：** 此接口为系统接口。

## fsType

```TypeScript
fsType: string
```

文件系统的类型，常见有ext2、vfat、NTFS等。

**说明**：从API version 24开始，支持ISO9660、UDF。

**类型：** string

**起始版本：** 12

**系统能力：** SystemCapability.FileManagement.StorageService.Volume

**系统接口：** 此接口为系统接口。

## id

```TypeScript
id: string
```

卷设备ID的格式为vol-{主设备号}-{次设备号}，主设备号用来区分不同种类的设备，
次设备号用来区分同一类型的多个设备，卷设备ID会随着插卡顺序不同而变化。

**类型：** string

**起始版本：** 9

**系统能力：** SystemCapability.FileManagement.StorageService.Volume

**系统接口：** 此接口为系统接口。

## path

```TypeScript
path: string
```

卷设备的挂载地址，一般为/mnt/data/external/{uuid}。

**类型：** string

**起始版本：** 9

**系统能力：** SystemCapability.FileManagement.StorageService.Volume

**系统接口：** 此接口为系统接口。

## removable

```TypeScript
removable: boolean
```

表示卷设备是否可移除，当前仅支持可移除存储设备。true为可移除；false为不可移除。

**类型：** boolean

**起始版本：** 9

**系统能力：** SystemCapability.FileManagement.StorageService.Volume

**系统接口：** 此接口为系统接口。

## state

```TypeScript
state: number
```

卷设备状态标识：

0：卸载状态 UNMOUNTED。

1：检查状态 CHECKING。

2：挂载状态 MOUNTED。

3：正在弹出状态 EJECTING。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.FileManagement.StorageService.Volume

**系统接口：** 此接口为系统接口。

## uuid

```TypeScript
uuid: string
```

卷设备uuid是卷设备的通用唯一识别码，不会随着插卡顺序变化而变化，但是卷设备的格式化会改变卷设备的uuid。

**类型：** string

**起始版本：** 9

**系统能力：** SystemCapability.FileManagement.StorageService.Volume

**系统接口：** 此接口为系统接口。

