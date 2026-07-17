# ArrowStyle

左右箭头属性。

**起始版本：** 10

<!--Device-unnamed-declare interface ArrowStyle--><!--Device-unnamed-declare interface ArrowStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## arrowColor

```TypeScript
arrowColor?: ResourceColor
```

设置箭头颜色。

默认值：'#182431'

**类型：** ResourceColor

**默认值：** #182431

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ArrowStyle-arrowColor?: ResourceColor--><!--Device-ArrowStyle-arrowColor?: ResourceColor-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## arrowSize

```TypeScript
arrowSize?: Length
```

设置箭头大小。

在导航点两侧显示时：

默认值：18vp

在组件两侧显示时：

默认值：24vp

**说明：**

showBackground为true时，arrowSize为backgroundSize的3/4。

不支持设置百分比。

**类型：** Length

**默认值：** When isSidebarMiddle is false, the default value is 18vp, Otherwise, the default value is 24vp

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ArrowStyle-arrowSize?: Length--><!--Device-ArrowStyle-arrowSize?: Length-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## backgroundColor

```TypeScript
backgroundColor?: ResourceColor
```

设置底板颜色。

在导航点两侧显示：

默认值：'#00000000'

在组件两侧显示：

默认值：'#19182431'

**类型：** ResourceColor

**默认值：** When isSidebarMiddle is false, the default value is #00000000, Otherwise,the default value is #1918243
1 [since 10 - 10]
@default When isSidebarMiddle is false, the default value is #00000000, Otherwise, the default value is #1918243
1 [since 11]

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ArrowStyle-backgroundColor?: ResourceColor--><!--Device-ArrowStyle-backgroundColor?: ResourceColor-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## backgroundSize

```TypeScript
backgroundSize?: Length
```

设置底板大小。

在导航点两侧显示：

默认值：24vp

在组件两侧显示：

默认值：32vp

不支持设置百分比。

**类型：** Length

**默认值：** When isSidebarMiddle is false, the default value is 24vp, Otherwise,the default value is 32vp

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ArrowStyle-backgroundSize?: Length--><!--Device-ArrowStyle-backgroundSize?: Length-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## isSidebarMiddle

```TypeScript
isSidebarMiddle?: boolean
```

设置箭头显示位置。为true时箭头居中显示在Swiper组件两侧，为false时显示在导航点指示器两侧。

默认值：false

默认显示在导航点指示器两侧。

**类型：** boolean

**默认值：** false

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ArrowStyle-isSidebarMiddle?: boolean--><!--Device-ArrowStyle-isSidebarMiddle?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## showBackground

```TypeScript
showBackground?: boolean
```

设置箭头底板是否显示。为true时箭头底板显示，为false时箭头底板不显示。

默认值：false

**类型：** boolean

**默认值：** false

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ArrowStyle-showBackground?: boolean--><!--Device-ArrowStyle-showBackground?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

