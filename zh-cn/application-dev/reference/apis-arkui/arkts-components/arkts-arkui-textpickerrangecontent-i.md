# TextPickerRangeContent

单列数据选择器的数据选项内容。

**起始版本：** 10

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## icon

```TypeScript
icon: string | Resource
```

图片资源。 icon是string类型时，表示图片存放的路径，例如"/common/hello.png"。

**类型：** string | Resource

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## text

```TypeScript
text?: string | Resource
```

文本信息。

默认值：空字符串

**说明**：当文本长度大于列宽时，文本被截断。

**类型：** string | Resource

**默认值：** ""

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

