# MarqueeUpdateStrategy

Marquee scrolling strategy after text update

**起始版本：** 12

<!--Device-unnamed-declare enum MarqueeUpdateStrategy--><!--Device-unnamed-declare enum MarqueeUpdateStrategy-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## DEFAULT

```TypeScript
DEFAULT = 0
```

Reset scroll position and restart scroll.

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-MarqueeUpdateStrategy-DEFAULT = 0--><!--Device-MarqueeUpdateStrategy-DEFAULT = 0-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## PRESERVE_POSITION

```TypeScript
PRESERVE_POSITION = 1
```

Preserve scroll position, just change to new text

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-MarqueeUpdateStrategy-PRESERVE_POSITION = 1--><!--Device-MarqueeUpdateStrategy-PRESERVE_POSITION = 1-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

