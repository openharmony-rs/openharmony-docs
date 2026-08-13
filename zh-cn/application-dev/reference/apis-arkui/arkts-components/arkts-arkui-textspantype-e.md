# TextSpanType

Span类型信息。 > **说明：** > > 菜单类型的匹配顺序如下。例如，用户长按文本时，根据以下规则查找： > > 1. 查找是否注册了TextSpanType.TEXT、TextResponseType.LONG_PRESS菜单 > > 2. 查找是否注册了TextSpanType.TEXT、TextResponseType.DEFAULT菜单 > > 3. 查找是否注册了TextSpanType.DEFAULT、TextResponseType.LONG_PRESS菜单 > > 4. 查找是否注册了TextSpanType.DEFAULT、TextResponseType.DEFAULT菜单

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

<!--Device-unnamed-declare enum TextSpanType--><!--Device-unnamed-declare enum TextSpanType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## TEXT

```TypeScript
TEXT = 0
```

Span为文字类型。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TextSpanType-TEXT = 0--><!--Device-TextSpanType-TEXT = 0-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## IMAGE

```TypeScript
IMAGE = 1
```

Span为图像类型。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TextSpanType-IMAGE = 1--><!--Device-TextSpanType-IMAGE = 1-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## MIXED

```TypeScript
MIXED = 2
```

Span为图文混合类型。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TextSpanType-MIXED = 2--><!--Device-TextSpanType-MIXED = 2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## DEFAULT

```TypeScript
DEFAULT = 3
```

注册此类型菜单但未注册TEXT、IMAGE、MIXED菜单时，文字类型、图片类型、图文混合类型都会触发并显示此类型对应的菜单。

**起始版本：** 15

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为15。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-TextSpanType-DEFAULT = 3--><!--Device-TextSpanType-DEFAULT = 3-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

