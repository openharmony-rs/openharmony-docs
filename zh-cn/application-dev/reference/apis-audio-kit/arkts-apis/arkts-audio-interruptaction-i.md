# InterruptAction

音频打断/获取焦点事件的回调方法。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** InterruptEvent

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

## actionType

```TypeScript
actionType: InterruptActionType
```

事件返回类型。TYPE_ACTIVATED为焦点触发事件，TYPE_INTERRUPT为音频打断事件。

**类型：** InterruptActionType

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

**替代接口：** hintType

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

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

