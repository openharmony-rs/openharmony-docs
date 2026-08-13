# CursorController

class CursorController

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare class CursorController--><!--Device-unnamed-export declare class CursorController-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## restoreDefault

```TypeScript
restoreDefault(): void
```

Restore default cursor.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CursorController-restoreDefault(): void--><!--Device-CursorController-restoreDefault(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## setCursor

```TypeScript
setCursor(value: PointerStyle): void
```

设置光标样式。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CursorController-setCursor(value: PointerStyle): void--><!--Device-CursorController-setCursor(value: PointerStyle): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [PointerStyle](../../apis-arkui/arkts-apis/arkts-arkui-pointerstyle-t.md) | 是 | cursor style enum. |

## setCustomCursor

```TypeScript
setCustomCursor(value: image.PixelMap, focusX?: int, focusY?: int): void
```

设置自定义光标样式。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CursorController-setCustomCursor(value: image.PixelMap, focusX?: int, focusY?: int): void--><!--Device-CursorController-setCustomCursor(value: image.PixelMap, focusX?: int, focusY?: int): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | image.PixelMap | 是 | 自定义光标样式。 |
| focusX | int | 否 | 自定义光标的焦点x。取值大于等于0。默认的 值为0。 |
| focusY | int | 否 | 自定义光标的焦点y。取值大于等于0。默认的 值为0。 |

