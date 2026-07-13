# DecodeToStringOptions

描述 **decodeToString** 方法在解码字节流时的行为参数。

**起始版本：** 12

**系统能力：** SystemCapability.Utils.Lang

## stream

```TypeScript
stream?: boolean
```

输入末尾出现的不完整字节序列是否需要追加在下次调用 **decodeToString** 的参数中处理。值为 **true** 表示不完整的字节
序列会存储在内部缓存区直到下次调用该函数。如果值为 false，则会在当前调用该函数时直接解码该字节序列。默认值为
**false**。

**类型：** boolean

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

