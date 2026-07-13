# Action

触屏输入事件类型。

**起始版本：** 9

**系统能力：** SystemCapability.MultimodalInput.Input.Core

## CANCEL

```TypeScript
CANCEL = 0
```

触屏取消。触屏down事件异常打断，未正常闭环，例如：手指按下后未抬起，屏幕发生旋转、折叠或有新hover等场景时触发cancel事件。

**起始版本：** 9

**系统能力：** SystemCapability.MultimodalInput.Input.Core

## DOWN

```TypeScript
DOWN = 1
```

触屏按下。

**起始版本：** 9

**系统能力：** SystemCapability.MultimodalInput.Input.Core

## MOVE

```TypeScript
MOVE = 2
```

触屏移动。

**起始版本：** 9

**系统能力：** SystemCapability.MultimodalInput.Input.Core

## UP

```TypeScript
UP = 3
```

触屏抬起。

**起始版本：** 9

**系统能力：** SystemCapability.MultimodalInput.Input.Core

## PULL_DOWN

```TypeScript
PULL_DOWN = 4
```

触屏开始拖拽。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.MultimodalInput.Input.Core

## PULL_MOVE

```TypeScript
PULL_MOVE = 5
```

触屏拖拽移动。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.MultimodalInput.Input.Core

## PULL_UP

```TypeScript
PULL_UP = 6
```

触屏结束拖拽。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.MultimodalInput.Input.Core

