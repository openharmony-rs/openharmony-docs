# InterruptAction

音频打断/获取焦点事件的回调方法。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** InterruptEvent

<!--Device-audio-interface InterruptAction--><!--Device-audio-interface InterruptAction-End-->

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

**类型：** InterruptActionType

**起始版本：** 7

**废弃版本：** 9

**替代接口：** eventType

<!--Device-InterruptAction-actionType: InterruptActionType--><!--Device-InterruptAction-actionType: InterruptActionType-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

## activated

```TypeScript
activated?: boolean
```

焦点获取/释放是否成功。true表示焦点获取/释放成功，false表示焦点获得/释放失败。

**类型：** boolean

**起始版本：** 7

**废弃版本：** 9

**替代接口：** hintType

<!--Device-InterruptAction-activated?: boolean--><!--Device-InterruptAction-activated?: boolean-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

## hint

```TypeScript
hint?: InterruptHint
```

打断事件提示。

**类型：** InterruptHint

**起始版本：** 7

**废弃版本：** 9

**替代接口：** hintType

<!--Device-InterruptAction-hint?: InterruptHint--><!--Device-InterruptAction-hint?: InterruptHint-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

## type

```TypeScript
type?: InterruptType
```

打断事件类型。

**类型：** InterruptType

**起始版本：** 7

**废弃版本：** 9

**替代接口：** eventType

<!--Device-InterruptAction-type?: InterruptType--><!--Device-InterruptAction-type?: InterruptType-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

