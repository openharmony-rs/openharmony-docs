# TextTimerController

TextTimer组件的控制器，用于控制文本计时器。一个TextTimer组件仅支持绑定一个控制器，组件创建完成后相关指令才能被调用。一个TextTimerController只能控制最后一个绑定此TextTimerController的TextTimer组件。

## 导入对象

```ts
textTimerController: TextTimerController = new TextTimerController()
```

**起始版本：** 8

<!--Device-unnamed-declare class TextTimerController--><!--Device-unnamed-declare class TextTimerController-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor()
```

TextTimerController的构造函数。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本10开始，该接口支持在ArkTS卡片中使用。

<!--Device-TextTimerController-constructor()--><!--Device-TextTimerController-constructor()-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## pause

```TypeScript
pause()
```

计时暂停。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本10开始，该接口支持在ArkTS卡片中使用。

<!--Device-TextTimerController-pause()--><!--Device-TextTimerController-pause()-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## reset

```TypeScript
reset()
```

重置计时器。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本10开始，该接口支持在ArkTS卡片中使用。

<!--Device-TextTimerController-reset()--><!--Device-TextTimerController-reset()-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## start

```TypeScript
start()
```

计时开始。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本10开始，该接口支持在ArkTS卡片中使用。

<!--Device-TextTimerController-start()--><!--Device-TextTimerController-start()-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

