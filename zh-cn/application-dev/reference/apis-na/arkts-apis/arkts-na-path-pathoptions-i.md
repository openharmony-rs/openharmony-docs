# PathOptions

用于描述Path组件绘制属性。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface PathOptions--><!--Device-unnamed-export declare interface PathOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## commands

```TypeScript
commands?: ResourceStr
```

路径绘制的命令字符串。 默认值：空字符串 异常值按照默认值处理。

**类型：** [ResourceStr](../../apis-arkui/arkts-apis/arkts-arkui-resourcestr-t.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PathOptions-commands?: ResourceStr--><!--Device-PathOptions-commands?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## height

```TypeScript
height?: Length
```

路径所在矩形的高度。 值为异常值或缺省时按照自身内容需要的高度处理。 默认单位：vp

**类型：** [Length](../../apis-arkui/arkts-apis/arkts-arkui-length-t.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PathOptions-height?: Length--><!--Device-PathOptions-height?: Length-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## width

```TypeScript
width?: Length
```

路径所在矩形的宽度。 值为异常值或缺省时按照自身内容需要的宽度处理。 默认单位：vp

**类型：** [Length](../../apis-arkui/arkts-apis/arkts-arkui-length-t.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PathOptions-width?: Length--><!--Device-PathOptions-width?: Length-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

