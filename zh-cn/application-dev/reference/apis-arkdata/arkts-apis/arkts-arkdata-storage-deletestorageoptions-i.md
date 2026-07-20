# DeleteStorageOptions

**起始版本：** 3

**废弃版本：** 6

<!--Device-unnamed-export interface DeleteStorageOptions--><!--Device-unnamed-export interface DeleteStorageOptions-End-->

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core.Lite

## complete

```TypeScript
complete?: () => void
```

接口调用结束的回调函数。

**类型：** () =&gt; void

**起始版本：** 3

**废弃版本：** 6

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-DeleteStorageOptions-complete?: () => void--><!--Device-DeleteStorageOptions-complete?: () => void-End-->

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core.Lite

## fail

```TypeScript
fail?: (data: string, code: number) => void
```

接口调用失败的回调函数，data为错误信息，code为错误码。

**类型：** (data: string, code: number) =&gt; void

**起始版本：** 3

**废弃版本：** 6

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-DeleteStorageOptions-fail?: (data: string, code: number) => void--><!--Device-DeleteStorageOptions-fail?: (data: string, code: number) => void-End-->

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

<!--Device-DeleteStorageOptions-key: string--><!--Device-DeleteStorageOptions-key: string-End-->

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core.Lite

## success

```TypeScript
success?: () => void
```

接口调用成功的回调函数。

**类型：** () =&gt; void

**起始版本：** 3

**废弃版本：** 6

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-DeleteStorageOptions-success?: () => void--><!--Device-DeleteStorageOptions-success?: () => void-End-->

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core.Lite

