# TabBarOptions

Array of tab bar container configurations.

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { AtomicServiceTabs, TabBarOptions, TabBarPosition, TabContentBuilder, OnContentWillChangeCallback } from '@kit.ArkUI';
```

## constructor

```TypeScript
constructor(icon: ResourceStr | TabBarSymbol, text: ResourceStr,
    unselectedColor?: ResourceColor, selectedColor?: ResourceColor)
```

A constructor used to create a **TabBarOptions** instance.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| icon | [ResourceStr](arkts-arkui-resourcestr-t.md) &#124; [TabBarSymbol](../arkts-components/arkts-arkui-tabbarsymbol-c.md) | Yes | Image for the tab. |
| text | [ResourceStr](arkts-arkui-resourcestr-t.md) | Yes | Text of the tab. |
| unselectedColor | [ResourceColor](arkts-arkui-resourcecolor-t.md) | No | Color of the tab when it is not selected.<br>Default value: **#99182431** |
| selectedColor | [ResourceColor](arkts-arkui-resourcecolor-t.md) | No | Color of the tab when it is selected.<br>Default value: **#FF007DFF** |
