# AccessModeType

```TypeScript
declare enum AccessModeType
```

枚举，表示需要校验的具体权限。若不填，默认校验文件是否存在。

**起始版本：** 12

**系统能力：** SystemCapability.FileManagement.File.FileIO

## EXIST

```TypeScript
EXIST = 0
```

文件是否存在。

**起始版本：** 12

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.FileManagement.File.FileIO

## WRITE

```TypeScript
WRITE = 2
```

文件是否具有写入权限。

**起始版本：** 12

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.FileManagement.File.FileIO

## READ

```TypeScript
READ = 4
```

文件是否具有读取权限。

**起始版本：** 12

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.FileManagement.File.FileIO

## READ_WRITE

```TypeScript
READ_WRITE = 6
```

文件是否具有读写权限。

**起始版本：** 12

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.FileManagement.File.FileIO

