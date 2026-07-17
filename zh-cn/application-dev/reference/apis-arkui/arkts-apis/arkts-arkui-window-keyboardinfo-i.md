# KeyboardInfo

软键盘窗口信息。

**起始版本：** 18

<!--Device-window-interface KeyboardInfo--><!--Device-window-interface KeyboardInfo-End-->

**系统能力：** SystemCapability.Window.SessionManager

## 导入模块

```TypeScript
import { window } from '@kit.ArkUI';
```

## animated

```TypeScript
animated?: boolean
```

当前是否有显示/隐藏动画，true表示有动画，false表示没有。

**类型：** boolean

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-KeyboardInfo-animated?: boolean--><!--Device-KeyboardInfo-animated?: boolean-End-->

**系统能力：** SystemCapability.Window.SessionManager

## beginRect

```TypeScript
beginRect: Rect
```

动画开始前软键盘的位置和大小。

**类型：** Rect

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-KeyboardInfo-beginRect: Rect--><!--Device-KeyboardInfo-beginRect: Rect-End-->

**系统能力：** SystemCapability.Window.SessionManager

## config

```TypeScript
config?: WindowAnimationConfig
```

动画配置信息。

**类型：** WindowAnimationConfig

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-KeyboardInfo-config?: WindowAnimationConfig--><!--Device-KeyboardInfo-config?: WindowAnimationConfig-End-->

**系统能力：** SystemCapability.Window.SessionManager

## endRect

```TypeScript
endRect: Rect
```

动画结束后软键盘的位置和大小。

**类型：** Rect

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-KeyboardInfo-endRect: Rect--><!--Device-KeyboardInfo-endRect: Rect-End-->

**系统能力：** SystemCapability.Window.SessionManager

