# ClearStorageOptions

**起始版本：** 3

**废弃版本：** 6

<!--Device-unnamed-export interface ClearStorageOptions--><!--Device-unnamed-export interface ClearStorageOptions-End-->

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

<!--Device-ClearStorageOptions-complete?: () => void--><!--Device-ClearStorageOptions-complete?: () => void-End-->

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

<!--Device-ClearStorageOptions-fail?: (data: string, code: number) => void--><!--Device-ClearStorageOptions-fail?: (data: string, code: number) => void-End-->

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

<!--Device-ClearStorageOptions-success?: () => void--><!--Device-ClearStorageOptions-success?: () => void-End-->

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core.Lite

