# AccessModeType

枚举，表示需要校验的具体权限。若不填，默认校验文件是否存在。

**起始版本：** 12

<!--Device-unnamed-declare enum AccessModeType--><!--Device-unnamed-declare enum AccessModeType-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## EXIST

```TypeScript
EXIST = 0
```

文件是否存在。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AccessModeType-EXIST = 0--><!--Device-AccessModeType-EXIST = 0-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## WRITE

```TypeScript
WRITE = 2
```

文件是否具有写入权限。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AccessModeType-WRITE = 2--><!--Device-AccessModeType-WRITE = 2-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## READ

```TypeScript
READ = 4
```

文件是否具有读取权限。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AccessModeType-READ = 4--><!--Device-AccessModeType-READ = 4-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## READ_WRITE

```TypeScript
READ_WRITE = 6
```

文件是否具有读写权限。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AccessModeType-READ_WRITE = 6--><!--Device-AccessModeType-READ_WRITE = 6-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

