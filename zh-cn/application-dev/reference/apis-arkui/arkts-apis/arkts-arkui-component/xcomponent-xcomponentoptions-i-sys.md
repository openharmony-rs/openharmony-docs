# XComponentOptions

定义XComponent的具体配置参数。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface XComponentOptions--><!--Device-unnamed-export declare interface XComponentOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## screenId

```TypeScript
screenId?: long
```

给组件设置关联屏幕ID，通过此项可在组件上显示关联屏幕画面。 屏幕ID可通过@ohos.screen模块的getAllScreens接口获取。 默认值：0，表示主屏幕。 **说明：** 仅type为SURFACE时有效。

**类型：** long

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-XComponentOptions-screenId?: long--><!--Device-XComponentOptions-screenId?: long-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

