# LocalizedBarrierDirection

定义支持镜像模式的屏障线的方向。  
| 名称 | 值 | 说明 | | ------ | -- | ----------------------------- | | START | 0 |屏障在其所有[referencedId](arkts-arkui-localizedbarrierstyle-i.md)的起始侧，LTR模式时为最左侧，RTL模式时为最右侧。| | END | 1 | 屏障在其所有[referencedId](arkts-arkui-localizedbarrierstyle-i.md)的结束侧，LTR模式时为最右侧，RTL模式时为最左侧。| | TOP | 2 | 屏障在其所有[referencedId](arkts-arkui-localizedbarrierstyle-i.md)的最上方。| | BOTTOM | 3 | 屏障在其所有[referencedId](arkts-arkui-localizedbarrierstyle-i.md)的最下方。|

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## START

```TypeScript
START = 0
```

The barrier is on the left (for left-to-right scripts) or right (for right-to-left scripts) side of all the referenced components specified by [referencedId](arkts-arkui-localizedbarrierstyle-i.md).

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## END

```TypeScript
END = 1
```

The barrier is on the right (for left-to-right scripts) or left (for right-to-left scripts) side of all the referenced components specified by [referencedId](arkts-arkui-localizedbarrierstyle-i.md).

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## TOP

```TypeScript
TOP = 2
```

The barrier is at the top of all the referenced components specified by [referencedId](arkts-arkui-localizedbarrierstyle-i.md).

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## BOTTOM

```TypeScript
BOTTOM = 3
```

The barrier is at the bottom of all the referenced components specified by [referencedId](arkts-arkui-localizedbarrierstyle-i.md).

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
