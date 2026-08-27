# StarStyleOptions

评分组件选中、未选中以及部分选中的星级样式。

> **说明：**
> 
> 为规范匿名对象的定义，API 18版本修改了此处的元素定义。其中，保留了历史匿名对象的起始版本信息，会出现外层元素

**起始版本：** 18

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## backgroundUri

```TypeScript
backgroundUri: ResourceStr
```

未选中的星级的图片路径，可由用户自定义或使用系统默认图片。从API version 20开始，该接口支持设置Resource资源。参考 示例3（通过Resource资源设置评分的样式） 代码。

**类型：** [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md)

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## foregroundUri

```TypeScript
foregroundUri: ResourceStr
```

选中的星级的图片路径，可由用户自定义或使用系统默认图片。从API version 20开始，该接口支持设置Resource资源。参考 示例3（通过Resource资源设置评分的样式） 代码。

**类型：** [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md)

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## secondaryUri

```TypeScript
secondaryUri?: ResourceStr
```

部分选中的星级的图片路径，可由用户自定义或使用系统默认图片。未设置时将优先使用backgroundUri，效果等同于仅设置foregroundUri和backgroundUri。从API version 20开始，该接口支持设置Resource资源。参考 示例3（通过Resource资源设置评分的样式） 代码。

**类型：** [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md)

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
