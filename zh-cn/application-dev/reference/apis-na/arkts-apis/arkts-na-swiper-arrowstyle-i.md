# ArrowStyle

Arrow object.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface ArrowStyle--><!--Device-unnamed-export declare interface ArrowStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## arrowColor

```TypeScript
arrowColor?: ResourceColor
```

设置箭头颜色。 默认值： '#182431'，深灰色。

**类型：** [ResourceColor](../../apis-arkui/arkts-apis/arkts-arkui-resourcecolor-t.md)

**默认值：** #182431

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArrowStyle-arrowColor?: ResourceColor--><!--Device-ArrowStyle-arrowColor?: ResourceColor-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## arrowSize

```TypeScript
arrowSize?: Length
```

设置箭头大小。 在导航点两侧显示时： 在导航点两侧显示时： 默认值：18vp 在组件两侧显示时： 默认值：24vp。

**类型：** [Length](../../apis-arkui/arkts-apis/arkts-arkui-length-t.md)

**默认值：** When isSidebarMiddle is false, the default value is 18vp, Otherwise, the default value is 24vp

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArrowStyle-arrowSize?: Length--><!--Device-ArrowStyle-arrowSize?: Length-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## backgroundColor

```TypeScript
backgroundColor?: ResourceColor
```

设置底板颜色。 在导航点两侧显示： 透明色. 在组件两侧显示： 默认值：'#19182431'，半透明深灰色。 默认值： '#00000000'。

**类型：** [ResourceColor](../../apis-arkui/arkts-apis/arkts-arkui-resourcecolor-t.md)

**默认值：** When isSidebarMiddle is false, the default value is #00000000, Otherwise, the default value is #19182431

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArrowStyle-backgroundColor?: ResourceColor--><!--Device-ArrowStyle-backgroundColor?: ResourceColor-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## backgroundSize

```TypeScript
backgroundSize?: Length
```

设置底板大小。 不支持设置百分比。 <br>在导航点两侧显示： 默认值：24vp 在组件两侧显示： 默认值：32vp。

**类型：** [Length](../../apis-arkui/arkts-apis/arkts-arkui-length-t.md)

**默认值：** When isSidebarMiddle is false, the default value is 24vp, Otherwise,the default value is 32vp

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArrowStyle-backgroundSize?: Length--><!--Device-ArrowStyle-backgroundSize?: Length-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## isSidebarMiddle

```TypeScript
isSidebarMiddle?: boolean
```

设置箭头显示位置。 true：箭头居中显示在Swiper组件两侧；false：箭头显示在导航点指示器两侧。 默认值： false。

**类型：** boolean

**默认值：** false

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArrowStyle-isSidebarMiddle?: boolean--><!--Device-ArrowStyle-isSidebarMiddle?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## showBackground

```TypeScript
showBackground?: boolean
```

设置箭头底板是否显示。 true：箭头底板显示；false：箭头底板不显示。 默认值： false。

**类型：** boolean

**默认值：** false

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArrowStyle-showBackground?: boolean--><!--Device-ArrowStyle-showBackground?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

