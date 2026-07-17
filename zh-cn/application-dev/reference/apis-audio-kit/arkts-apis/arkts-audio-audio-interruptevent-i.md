# InterruptEvent

音频中断时，应用接收的中断事件。

**起始版本：** 9

<!--Device-audio-interface InterruptEvent--><!--Device-audio-interface InterruptEvent-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

## 导入模块

```TypeScript
import { audio } from '@kit.AudioKit';
```

## eventType

```TypeScript
eventType: InterruptType
```

音频中断事件类型，开始或是结束。

**类型：** InterruptType

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-InterruptEvent-eventType: InterruptType--><!--Device-InterruptEvent-eventType: InterruptType-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

## forceType

```TypeScript
forceType: InterruptForceType
```

操作是由系统强制执行或是由应用程序执行。

**类型：** InterruptForceType

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-InterruptEvent-forceType: InterruptForceType--><!--Device-InterruptEvent-forceType: InterruptForceType-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

## hintType

```TypeScript
hintType: InterruptHint
```

中断提示，用于提供中断事件的相关信息。

**类型：** InterruptHint

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-InterruptEvent-hintType: InterruptHint--><!--Device-InterruptEvent-hintType: InterruptHint-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

