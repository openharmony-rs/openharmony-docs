# InterruptAction

音频打断/获取焦点事件的回调方法。

> **说明：**
> 
> 从API version 7开始支持，从API version 9开始废弃，建议使用[InterruptEvent](arkts-audio-audio-interruptevent-i.md)替代。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [InterruptEvent](arkts-audio-audio-interruptevent-i.md)

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

## 导入模块

```TypeScript
import { audio } from '@kit.AudioKit';
```

## actionType

```TypeScript
actionType: InterruptActionType
```

事件返回类型。TYPE_ACTIVATED为焦点触发事件，TYPE_INTERRUPT为音频打断事件。

**类型：** [InterruptActionType](arkts-audio-audio-interruptactiontype-e.md)

**起始版本：** 7

**废弃版本：** 9

**替代接口：** eventType

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

## activated

```TypeScript
activated?: boolean
```

焦点获取/释放是否成功。true表示焦点获取/释放成功，false表示焦点获得/释放失败。

**类型：** boolean

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [hintType](arkts-audio-audio-interruptevent-i.md#hinttype)

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

## hint

```TypeScript
hint?: InterruptHint
```

打断事件提示。

**类型：** [InterruptHint](arkts-audio-audio-interrupthint-e.md)

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [hintType](arkts-audio-audio-interruptevent-i.md#hinttype)

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

## type

```TypeScript
type?: InterruptType
```

打断事件类型。

**类型：** [InterruptType](arkts-audio-audio-interrupttype-e.md)

**起始版本：** 7

**废弃版本：** 9

**替代接口：** eventType

**系统能力：** SystemCapability.Multimedia.Audio.Renderer
