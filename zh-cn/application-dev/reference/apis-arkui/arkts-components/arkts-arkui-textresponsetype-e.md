# TextResponseType

选择菜单的响应类型。
> **说明：**  
>  
> 菜单类型的匹配顺序如下。例如，用户长按文本时，根据以下规则查找：  
>

**起始版本：** 11

<!--Device-unnamed-declare enum TextResponseType--><!--Device-unnamed-declare enum TextResponseType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## RIGHT_CLICK

```TypeScript
RIGHT_CLICK = 0
```

通过鼠标右键触发菜单弹出。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TextResponseType-RIGHT_CLICK = 0--><!--Device-TextResponseType-RIGHT_CLICK = 0-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## LONG_PRESS

```TypeScript
LONG_PRESS = 1
```

通过长按触发菜单弹出。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TextResponseType-LONG_PRESS = 1--><!--Device-TextResponseType-LONG_PRESS = 1-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## SELECT

```TypeScript
SELECT = 2
```

通过鼠标选中触发菜单弹出。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TextResponseType-SELECT = 2--><!--Device-TextResponseType-SELECT = 2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## DEFAULT

```TypeScript
DEFAULT = 3
```

注册此类型的菜单，但未注册RIGHT_CLICK、LONG_PRESS、SELECT时，右键、长按、鼠标、[selection](TextAttribute#selection)选中均会触发并显示此类型对应的菜单。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-TextResponseType-DEFAULT = 3--><!--Device-TextResponseType-DEFAULT = 3-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

