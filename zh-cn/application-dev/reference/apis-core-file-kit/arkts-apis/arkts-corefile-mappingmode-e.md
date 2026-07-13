# MappingMode

枚举，文件内存映射模式类型，支持mmap接口使用。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.FileManagement.File.FileIO

## READ_ONLY

```TypeScript
READ_ONLY = 0
```

只读映射模式。文件映射区不可写，修改会抛出异常。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.FileManagement.File.FileIO

## READ_WRITE

```TypeScript
READ_WRITE = 1
```

读写映射模式。修改会写入文件映射区，后续由操作系统同步到文件（非实时）。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.FileManagement.File.FileIO

## PRIVATE

```TypeScript
PRIVATE = 2
```

私有映射模式。是一种写时复制的映射机制，对映射区的修改仅对当前进程可见，不会影响原始文件。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.FileManagement.File.FileIO

