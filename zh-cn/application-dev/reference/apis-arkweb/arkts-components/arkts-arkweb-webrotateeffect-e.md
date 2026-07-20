# WebRotateEffect

组件旋转时，宽高动画过程中组件内容如何填充以适应新尺寸的方式。

**起始版本：** 22

<!--Device-unnamed-declare enum WebRotateEffect--><!--Device-unnamed-declare enum WebRotateEffect-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## TOPLEFT_EFFECT

```TypeScript
TOPLEFT_EFFECT = 0
```

默认值，组件旋转时，保持动画终态的内容大小，并且内容始终与组件保持左上角对齐。

**起始版本：** 22

<!--Device-WebRotateEffect-TOPLEFT_EFFECT = 0--><!--Device-WebRotateEffect-TOPLEFT_EFFECT = 0-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## RESIZE_COVER_EFFECT

```TypeScript
RESIZE_COVER_EFFECT = 1
```

组件旋转时，保持动画终态内容的宽高比进行缩小或放大，使内容两边都大于或等于组件两边，且与组件保持中心对齐，显示内容的中间部分。

**起始版本：** 22

<!--Device-WebRotateEffect-RESIZE_COVER_EFFECT = 1--><!--Device-WebRotateEffect-RESIZE_COVER_EFFECT = 1-End-->

**系统能力：** SystemCapability.Web.Webview.Core

