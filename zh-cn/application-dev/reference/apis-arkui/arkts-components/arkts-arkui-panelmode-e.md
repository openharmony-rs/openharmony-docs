# PanelMode

设置可滑动面板的初始状态

> **说明：** 
> 
> 从API version 7开始支持，从API version 12开始废弃。

**起始版本：** 7

**废弃版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Mini

```TypeScript
Mini = 0
```

类型为Minibar和Foldable时，为最小状态；类型为Temporary，则不生效。

**起始版本：** 7

**废弃版本：** 12

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Half

```TypeScript
Half
```

类型为Foldable和Temporary时，为类半屏状态；类型为Minibar，则不生效。

**起始版本：** 7

**废弃版本：** 12

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Full

```TypeScript
Full
```

类型为Minibar、Foldable和Temporary时，为类全屏状态；类型为CUSTOM，则不生效。

**起始版本：** 7

**废弃版本：** 12

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
