# GestureMask

定义是否屏蔽子组件手势。

**起始版本：** 7

<!--Device-unnamed-declare enum GestureMask--><!--Device-unnamed-declare enum GestureMask-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Normal

```TypeScript
Normal
```

不屏蔽子组件的手势，按照默认手势识别顺序进行识别。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-GestureMask-Normal--><!--Device-GestureMask-Normal-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## IgnoreInternal

```TypeScript
IgnoreInternal
```

屏蔽子组件的手势，包括子组件上系统内置的手势，如子组件为List组件时，内置的滑动手势同样会被屏蔽。 若父子组件区域存在部分重叠，则只会屏蔽父子组件重叠的部分。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-GestureMask-IgnoreInternal--><!--Device-GestureMask-IgnoreInternal-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

