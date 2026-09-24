# MenuOptions

```TypeScript
declare interface MenuOptions extends ContextMenuOptions
```

Configues menu item information, which is inherited from [ContextMenuOptions](arkts-arkui-common-comp-contextmenuoptions-i.md).

@extends ContextMenuOptions @interface MenuOptions

**Inheritance/Implementation:** MenuOptions extends [ContextMenuOptions](arkts-arkui-common-comp-contextmenuoptions-i.md)

**Since:** 10

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## showInSubWindow

```TypeScript
showInSubWindow?: boolean
```

Whether to show the menu in a subwindow.

**true**: yes; **false**: no

Default value: **true** for 2-in-1 devices and **false** for other devices

**NOTE:** 

This parameter takes effect only for 2-in-1 devices.

**Type:** boolean

**Default:** 
- API version 12+: true for 2-in-1 devices

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## title

```TypeScript
title?: ResourceStr
```

Menu title.

**NOTE:** 

This parameter is effective only when **content** is set to Array&lt;[MenuElement](arkts-arkui-common-comp-menuelement-i.md)&gt;.

**Type:** [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
