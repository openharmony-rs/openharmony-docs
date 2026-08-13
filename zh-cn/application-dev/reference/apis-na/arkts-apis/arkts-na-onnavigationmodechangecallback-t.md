# OnNavigationModeChangeCallback

```TypeScript
declare type OnNavigationModeChangeCallback = (mode: NavigationMode) => void
```

当MultiNavigation的mode变化时触发的回调函数。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-declare type OnNavigationModeChangeCallback = (mode: NavigationMode) => void--><!--Device-unnamed-declare type OnNavigationModeChangeCallback = (mode: NavigationMode) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | NavigationMode | 是 | 当回调触发时的NavigationMode。 |

