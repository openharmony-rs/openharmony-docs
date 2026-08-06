# SwipeEdgeEffect

滑动效果枚举。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

<!--Device-unnamed-declare enum SwipeEdgeEffect--><!--Device-unnamed-declare enum SwipeEdgeEffect-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Spring

```TypeScript
Spring
```

ListItem划动距离超过划出组件大小后可以继续划动。 如果设置了删除区域，ListItem划动距离超过删除阈值后可以继续划动， 松手后按照弹簧阻尼曲线回弹。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SwipeEdgeEffect-Spring--><!--Device-SwipeEdgeEffect-Spring-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## None

```TypeScript
None
```

ListItem划动距离不能超过划出组件大小。 如果设置了删除区域，ListItem划动距离不能超过删除阈值， 并且在设置删除回调的情况下，达到删除阈值后松手触发删除回调。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SwipeEdgeEffect-None--><!--Device-SwipeEdgeEffect-None-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

