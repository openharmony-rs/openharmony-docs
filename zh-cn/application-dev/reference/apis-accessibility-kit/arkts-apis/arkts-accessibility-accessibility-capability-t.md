# Capability

```TypeScript
type Capability = 'retrieve' | 'touchGuide' | 'keyEventObserver' | 'zoom' | 'gesture'
```

辅助应用能力类型。

**起始版本：** 7

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本23开始，该接口支持在ArkTS卡片中使用。

<!--Device-accessibility-type Capability = 'retrieve' | 'touchGuide' | 'keyEventObserver' | 'zoom' | 'gesture'--><!--Device-accessibility-type Capability = 'retrieve' | 'touchGuide' | 'keyEventObserver' | 'zoom' | 'gesture'-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

| 类型 | 说明 |
| --- | --- |
| 'retrieve' | 具有检索窗口内容的能力。 |
| 'touchGuide' | 具有触摸探索模式的能力。 |
| 'keyEventObserver' | 具有过滤按键事件的能力。 |
| 'zoom' | 具有控制显示放大的能力，当前版本暂不支持。 |
| 'gesture' | 具有执行手势动作的能力。 |

