# PathOptions

用于描述Path组件绘制属性。
> **说明：**  
>  
> 为规范匿名对象的定义，API 18版本修改了此处的元素定义。其中，保留了历史匿名对象的起始版本信息，会出现外层元素@since版本号高于内层元素版本号的情况，但这不影响接口的使用。

**起始版本：** 18

<!--Device-unnamed-declare interface PathOptions--><!--Device-unnamed-declare interface PathOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## commands

```TypeScript
commands?: ResourceStr
```

路径绘制的命令字符串。

值为异常值或缺省时按照自身内容需要的宽高处理。默认值：空字符串

异常值按照默认值处理。

**类型：** ResourceStr

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-PathOptions-commands?: ResourceStr--><!--Device-PathOptions-commands?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## height

```TypeScript
height?: Length
```

路径所在矩形的高度。

值为异常值或缺省时按照自身内容需要的高度处理。

默认单位：vp

**类型：** Length

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-PathOptions-height?: Length--><!--Device-PathOptions-height?: Length-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## width

```TypeScript
width?: Length
```

路径所在矩形的宽度。

值为异常值或缺省时按照自身内容需要的宽度处理。

默认单位：vp

**类型：** Length

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-PathOptions-width?: Length--><!--Device-PathOptions-width?: Length-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

