# DlpAtomicPermissionType

```TypeScript
export enum DlpAtomicPermissionType
```

枚举DLP文件的原子权限，包括用户操作和应用权限控制。该枚举支持按位OR操作，以组合多个权限。

**起始版本：** 26.1.0

<!--Device-dlpPermission-export enum DlpAtomicPermissionType--><!--Device-dlpPermission-export enum DlpAtomicPermissionType-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

## ATOMIC_APP_PERMISSION

```TypeScript
ATOMIC_APP_PERMISSION = 0x20
```

原子权限，允许沙箱应用访问被限制的系统服务。访问DLP文件时，系统会创建应用的独立沙箱，该沙箱继承应用的数据、配置和权限。该标志位允许沙箱在继承的权限内访问系统服务。例如，如果原始应用没有使用蓝牙权限，那么即使启用此标志，沙箱应用也无法调用蓝牙相关API。具体包括以下权限：-访问互联网，设置Wi-Fi配置，设置Wi-Fi信息，管理Wi-Fi热点权限。-使用蓝牙，管理蓝牙，访问蓝牙，发现蓝牙权限。-访问NearLink并管理NearLink权限。-使用云公共服务、使用云备份服务、使用云硬盘服务、云文件同步、云文件同步管理器权限。-发送消息、接收短信、接收彩信、接收WAP消息权限。-写入音频、写入文档、写入图像/视频和写入媒体权限。-读写下载目录、读写桌面目录、读写文档目录权限。-写入整个日历权限。-代理授权URI权限。-文件访问管理器权限。-分布式数据同步权限。  
- NFC标签权限。

该权限可以与其他原子权限使用按位或运算组合。查看 [DLP服务开发指导](../../../security/DataProtectionKit/dlp-guidelines.md)

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DlpAtomicPermissionType-ATOMIC_APP_PERMISSION = 0x20--><!--Device-DlpAtomicPermissionType-ATOMIC_APP_PERMISSION = 0x20-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

## ATOMIC_COPY

```TypeScript
ATOMIC_COPY = 0x04
```

复制文件内容的原子权限。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DlpAtomicPermissionType-ATOMIC_COPY = 0x04--><!--Device-DlpAtomicPermissionType-ATOMIC_COPY = 0x04-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

## ATOMIC_EDIT

```TypeScript
ATOMIC_EDIT = 0x02
```

文件编辑原子权限。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DlpAtomicPermissionType-ATOMIC_EDIT = 0x02--><!--Device-DlpAtomicPermissionType-ATOMIC_EDIT = 0x02-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

## ATOMIC_PRINT

```TypeScript
ATOMIC_PRINT = 0x10
```

打印文件的原子权限。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DlpAtomicPermissionType-ATOMIC_PRINT = 0x10--><!--Device-DlpAtomicPermissionType-ATOMIC_PRINT = 0x10-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

## ATOMIC_READ

```TypeScript
ATOMIC_READ = 0x01
```

读取文件的原子权限。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DlpAtomicPermissionType-ATOMIC_READ = 0x01--><!--Device-DlpAtomicPermissionType-ATOMIC_READ = 0x01-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

## ATOMIC_SCREENSHOT

```TypeScript
ATOMIC_SCREENSHOT = 0x08
```

截图文件的原子权限。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DlpAtomicPermissionType-ATOMIC_SCREENSHOT = 0x08--><!--Device-DlpAtomicPermissionType-ATOMIC_SCREENSHOT = 0x08-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention
