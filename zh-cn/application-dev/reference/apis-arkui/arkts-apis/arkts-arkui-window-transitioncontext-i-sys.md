# TransitionContext（系统接口）

属性转换的上下文信息。

**起始版本：** 9

<!--Device-window-interface TransitionContext--><!--Device-window-interface TransitionContext-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { window } from '@kit.ArkUI';
```

<a id="completetransition"></a>
## completeTransition

```TypeScript
completeTransition(isCompleted: boolean): void
```

设置属性转换的最终完成状态。该函数需要在动画函数[animateTo()](../../apis-arkui/arkts-components/arkts-arkui-common-attribute.md)执行后设置。

**起始版本：** 9

<!--Device-TransitionContext-completeTransition(isCompleted: boolean): void--><!--Device-TransitionContext-completeTransition(isCompleted: boolean): void-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isCompleted | boolean | 是 | 窗口属性转换是否完成。true表示完成本次转换；false表示撤销本次转换。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API.<br>**适用版本：** 12+ |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types. |

**示例：**

```TypeScript
(context: window.TransitionContext) => {
  let toWindow: window.Window = context.toWindow;
  this.getUIContext()?.animateTo({
    duration: 1000, // 动画时长
    tempo: 0.5, // 播放速率
    curve: Curve.EaseInOut, // 动画曲线
    delay: 0, // 动画延迟
    iterations: 1, // 播放次数
    playMode: PlayMode.Normal, // 动画模式
  }, () => {
    let obj: window.TranslateOptions = {
      x: 100.0,
      y: 0.0,
      z: 0.0
    };
    toWindow?.translate(obj);
    console.info('toWindow translate end');
  }
  );
  try {
    context.completeTransition(true)
  } catch (exception) {
    console.error(`toWindow translate fail. Cause code: ${exception.code}, message: ${exception.message}`);
  }
  console.info('complete transition end');
};

```

## toWindow

```TypeScript
toWindow: Window
```

动画的目标窗口。

**类型：** Window

**起始版本：** 9

<!--Device-TransitionContext-toWindow: Window--><!--Device-TransitionContext-toWindow: Window-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

