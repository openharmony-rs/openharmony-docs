# StarStyleOptions

评分组件选中、未选中以及部分选中的星级样式。 > **说明：** > > 为规范匿名对象的定义，API 18版本修改了此处的元素定义。其中，保留了历史匿名对象的起始版本信息，会出现外层元素@since版本号高于内层元素版本号的情况，但这不影响接口的使用。 > **说明：** > > string格式可用于加载网络图片和本地图片。当使用相对路径引用本地图片时，例如Image("common/test.jpg")，其中common目录与pages同级，同时支持Base64字符串。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface StarStyleOptions--><!--Device-unnamed-export declare interface StarStyleOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## backgroundUri

```TypeScript
backgroundUri: ResourceStr | undefined
```

未选中的星级的图片链接，可由用户自定义或使用系统默认图片。取值为undefined时，则使用系统默认图片。 **卡片能力（仅ArkTS-Dyn）：** 从API version 9开始，该接口支持在ArkTS卡片中使用。 **原子化服务API（仅ArkTS-Dyn）：** 从API version 11开始，该接口支持在原子化服务中使用。 从API version 20开始，该接口支持设置Resource资源。参考 示例3（通过Resource资源设置评分的样式） 代码。

**类型：** [ResourceStr](../../apis-arkui/arkts-apis/arkts-arkui-resourcestr-t.md) \| undefined

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-StarStyleOptions-backgroundUri: ResourceStr | undefined--><!--Device-StarStyleOptions-backgroundUri: ResourceStr | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## foregroundUri

```TypeScript
foregroundUri: ResourceStr | undefined
```

选中的星级的图片路径，可由用户自定义或使用系统默认图片。取值为undefined时，则使用系统默认图片。 **卡片能力（仅ArkTS-Dyn）：** 从API version 9开始，该接口支持在ArkTS卡片中使用。 **原子化服务API（仅ArkTS-Dyn）：** 从API version 11开始，该接口支持在原子化服务中使用。 从API version 20开始，该接口支持设置Resource资源。参考 示例3（通过Resource资源设置评分的样式） 代码。

**类型：** [ResourceStr](../../apis-arkui/arkts-apis/arkts-arkui-resourcestr-t.md) \| undefined

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-StarStyleOptions-foregroundUri: ResourceStr | undefined--><!--Device-StarStyleOptions-foregroundUri: ResourceStr | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## secondaryUri

```TypeScript
secondaryUri?: ResourceStr
```

部分选中的星级的图片路径，可由用户自定义或使用系统默认图片。 **卡片能力（仅ArkTS-Dyn）：** 从API version 9开始，该接口支持在ArkTS卡片中使用。 **原子化服务API（仅ArkTS-Dyn）：** 从API version 11开始，该接口支持在原子化服务中使用。 从API version 20开始，该接口支持设置Resource资源。参考 示例3（通过Resource资源设置评分的样式） 代码。

**类型：** [ResourceStr](../../apis-arkui/arkts-apis/arkts-arkui-resourcestr-t.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-StarStyleOptions-secondaryUri?: ResourceStr--><!--Device-StarStyleOptions-secondaryUri?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

