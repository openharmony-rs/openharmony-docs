# GetStorageOptions

**起始版本：** 3

**废弃版本：** 6

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core.Lite

## 导入模块

```TypeScript
```

## complete

```TypeScript
complete?: () => void
```

接口调用结束的回调函数。

**起始版本：** 3

**废弃版本：** 6

**模型约束：** 此接口仅可在FA模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core.Lite

## fail

```TypeScript
fail?: (data: string, code: number) => void
```

接口调用失败的回调函数，data为错误信息，code为错误码。

**起始版本：** 3

**废弃版本：** 6

**模型约束：** 此接口仅可在FA模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core.Lite

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | string | 是 |  |
| code | number | 是 |  |

## success

```TypeScript
success?: (data: any) => void
```

接口调用成功的回调函数，data为返回key对应的value。

**起始版本：** 3

**废弃版本：** 6

**模型约束：** 此接口仅可在FA模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core.Lite

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | any | 是 |  |

## default

```TypeScript
default?: string
```

key不存在则返回的默认值。

**类型：** string

**起始版本：** 3

**废弃版本：** 6

**模型约束：** 此接口仅可在FA模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core.Lite

## key

```TypeScript
key: string
```

内容索引。

**类型：** string

**起始版本：** 3

**废弃版本：** 6

**模型约束：** 此接口仅可在FA模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core.Lite
