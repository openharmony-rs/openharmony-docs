# InterceptionModeCallback

```TypeScript
export type InterceptionModeCallback = (mode: NavigationMode) => void
```

Navigation单双栏显示状态发生变更时的拦截回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export type InterceptionModeCallback = (mode: NavigationMode) => void--><!--Device-unnamed-export type InterceptionModeCallback = (mode: NavigationMode) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | [NavigationMode](arkts-na-navigation-navigationmode-e.md) | 是 | 导航页的显示模式。 |

