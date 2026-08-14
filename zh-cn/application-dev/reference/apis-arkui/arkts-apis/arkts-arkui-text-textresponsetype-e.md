# TextResponseType

选择菜单的响应类型。 > **说明：** > > 菜单类型的匹配顺序如下。例如，用户长按文本时，根据以下规则查找： > > 1. 查找是否注册了TextSpanType.TEXT、TextResponseType.LONG_PRESS菜单 > > 2. 查找是否注册了TextSpanType.TEXT、TextResponseType.DEFAULT菜单 > > 3. 查找是否注册了TextSpanType.DEFAULT、TextResponseType.LONG_PRESS菜单 > > 4. 查找是否注册了TextSpanType.DEFAULT、TextResponseType.DEFAULT菜单

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare enum TextResponseType--><!--Device-unnamed-export declare enum TextResponseType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## RIGHT_CLICK

```TypeScript
RIGHT_CLICK = 0
```

通过鼠标右键触发菜单弹出。 **原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TextResponseType-RIGHT_CLICK = 0--><!--Device-TextResponseType-RIGHT_CLICK = 0-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## LONG_PRESS

```TypeScript
LONG_PRESS = 1
```

通过长按触发菜单弹出。 **原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TextResponseType-LONG_PRESS = 1--><!--Device-TextResponseType-LONG_PRESS = 1-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## SELECT

```TypeScript
SELECT = 2
```

通过鼠标选中触发菜单弹出。 **原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TextResponseType-SELECT = 2--><!--Device-TextResponseType-SELECT = 2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## DEFAULT

```TypeScript
DEFAULT = 3
```

注册此类型的菜单，但未注册RIGHT_CLICK、LONG_PRESS、SELECT时，右键、长按、鼠标、selection选中均会触发并显示此类型对应的菜单。 **原子化服务API（仅ArkTS-Dyn）：** 从API version 15开始，该接口支持在原子化服务中使用。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TextResponseType-DEFAULT = 3--><!--Device-TextResponseType-DEFAULT = 3-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

