# KeyFramePolicy

关键帧的策略配置。

**起始版本：** 20

<!--Device-window-interface KeyFramePolicy--><!--Device-window-interface KeyFramePolicy-End-->

**系统能力：** SystemCapability.Window.SessionManager

## 导入模块

```TypeScript
import { window } from '@kit.ArkUI';
```

## animationDelay

```TypeScript
animationDelay?: number
```

设置关键帧布局切换动效延迟时间，单位为毫秒，默认值为100。取值为0或正整数，浮点数向下取整。

**类型：** number

**默认值：** 100

**起始版本：** 20

<!--Device-KeyFramePolicy-animationDelay?: long--><!--Device-KeyFramePolicy-animationDelay?: long-End-->

**系统能力：** SystemCapability.Window.SessionManager

## animationDuration

```TypeScript
animationDuration?: number
```

设置关键帧布局的动效切换时间，单位为毫秒，默认值为100。取值为0或正整数，浮点数向下取整。

**类型：** number

**默认值：** 100

**起始版本：** 20

<!--Device-KeyFramePolicy-animationDuration?: long--><!--Device-KeyFramePolicy-animationDuration?: long-End-->

**系统能力：** SystemCapability.Window.SessionManager

## distance

```TypeScript
distance?: number
```

设置关键帧布局切换的拖拽距离间隔，单位为px，默认值为1000。取值为0或正整数，浮点数向下取整。设置为0时，忽略拖拽距离因素。与interval判断为或的关系：满足其一即开始布局切换。

**类型：** number

**默认值：** 1000

**起始版本：** 20

<!--Device-KeyFramePolicy-distance?: int--><!--Device-KeyFramePolicy-distance?: int-End-->

**系统能力：** SystemCapability.Window.SessionManager

## enable

```TypeScript
enable: boolean
```

是否开启关键帧。true表示开启，false表示关闭。

**类型：** boolean

**起始版本：** 20

<!--Device-KeyFramePolicy-enable: boolean--><!--Device-KeyFramePolicy-enable: boolean-End-->

**系统能力：** SystemCapability.Window.SessionManager

## interval

```TypeScript
interval?: number
```

设置关键帧布局切换的拖拽时间间隔，单位为毫秒，默认值为1000。取值为正整数，浮点数向下取整。与distance判断为或的关系：满足其一即开始布局切换。

**类型：** number

**默认值：** 1000

**起始版本：** 20

<!--Device-KeyFramePolicy-interval?: long--><!--Device-KeyFramePolicy-interval?: long-End-->

**系统能力：** SystemCapability.Window.SessionManager

