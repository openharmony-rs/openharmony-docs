# MenuItemGroupOptions

```TypeScript
declare interface MenuItemGroupOptions
```

Describes the header and footer information of the menu item group.

**Since:** 9

<!--Device-unnamed-declare interface MenuItemGroupOptions--><!--Device-unnamed-declare interface MenuItemGroupOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## footer

```TypeScript
footer?: ResourceStr | CustomBuilder
```

Footer information of the menu item group, which is displayed at the bottom of all menu items in the group.

If not set, no footer is displayed.

**Type:** [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) &#124; [CustomBuilder](arkts-arkui-common-comp-custombuilder-t.md)

**Since:** 9

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-MenuItemGroupOptions-footer?: ResourceStr | CustomBuilder--><!--Device-MenuItemGroupOptions-footer?: ResourceStr | CustomBuilder-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## header

```TypeScript
header?: ResourceStr | CustomBuilder
```

Header information of the menu item group, which is displayed at the top of all menu items in the group.

If not set, no header is displayed.

**Type:** [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) &#124; [CustomBuilder](arkts-arkui-common-comp-custombuilder-t.md)

**Since:** 9

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-MenuItemGroupOptions-header?: ResourceStr | CustomBuilder--><!--Device-MenuItemGroupOptions-header?: ResourceStr | CustomBuilder-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
