# CacheStrategy

表示缓存刷新策略的枚举。

**起始版本：** 23

**系统能力：** SystemCapability.Request.FileTransferAgent

## FORCE

```TypeScript
FORCE = 0
```

强制更新缓存，无论缓存是否已经存在。

**起始版本：** 23

**系统能力：** SystemCapability.Request.FileTransferAgent

## LAZY

```TypeScript
LAZY = 1
```

延迟更新缓存，只有当缓存不存在时才会更新。

**起始版本：** 23

**系统能力：** SystemCapability.Request.FileTransferAgent

