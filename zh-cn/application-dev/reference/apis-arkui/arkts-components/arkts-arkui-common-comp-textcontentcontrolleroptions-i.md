# TextContentControllerOptions

```TypeScript
declare interface TextContentControllerOptions
```

用于设置输入框插入字符时的配置选项。

**起始版本：** 15

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## offset

```TypeScript
offset?: number
```

插入文本的位置，取值范围[0, 文本长度]。超出范围时自动修正到有效边界位置。

> **说明：** 
> 
> 当需要在指定位置（而非末尾）插入文本时传入此参数。不传入时默认插入到文本末尾。

**类型：** number

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
