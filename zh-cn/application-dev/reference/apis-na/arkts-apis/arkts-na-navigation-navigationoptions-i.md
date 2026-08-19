# NavigationOptions

路由栈操作选项。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface NavigationOptions--><!--Device-unnamed-export declare interface NavigationOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## animated

```TypeScript
animated?: boolean
```

是否支持转场动画。 true：支持转场动画；false：不支持转场动画。 默认值：true

**类型：** boolean

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavigationOptions-animated?: boolean--><!--Device-NavigationOptions-animated?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## launchMode

```TypeScript
launchMode?: LaunchMode
```

路由栈的操作模式。 默认值： LaunchMode.STANDARD。

**类型：** [LaunchMode](arkts-na-navigation-launchmode-e.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavigationOptions-launchMode?: LaunchMode--><!--Device-NavigationOptions-launchMode?: LaunchMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

