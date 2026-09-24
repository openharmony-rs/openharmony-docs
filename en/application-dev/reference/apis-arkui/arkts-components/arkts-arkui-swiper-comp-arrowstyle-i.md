# ArrowStyle

```TypeScript
declare interface ArrowStyle
```

Describes the left and right arrow attributes.

**Since:** 10

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## arrowColor

```TypeScript
arrowColor?: ResourceColor
```

Color of the arrow.

Default value: **'#182431'**

**Type:** [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md)

**Default:** #182431

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## arrowSize

```TypeScript
arrowSize?: Length
```

Size of the arrow.

On both sides of the navigation indicator:

Default value: **18vp**.

On both sides of the component:

Default value: **24vp**.

**NOTE:** 

If **showBackground** is set to **true**, the value of **arrowSize** is 3/4 of the value of **backgroundSize**.

Percentage values are not supported.

**Type:** [Length](../arkts-apis/arkts-arkui-length-t.md)

**Default:** When isSidebarMiddle is false, the default value is 18vp, Otherwise, the default value is 24vp

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## backgroundColor

```TypeScript
backgroundColor?: ResourceColor
```

Color of the background.

On both sides of the navigation indicator:

Default value: **'#00000000'**.

On both sides of the component:

Default value: **'#19182431'**.

**Type:** [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md)

**Default:** 
- API version 10: When isSidebarMiddle is false, the default value is #00000000, Otherwise,the default value is #19182431
- API version 11+: When isSidebarMiddle is false, the default value is #00000000, Otherwise, the default value is #19182431

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## backgroundSize

```TypeScript
backgroundSize?: Length
```

Size of the background.

On both sides of the navigation indicator:

Default value: **24vp**.

On both sides of the component:

Default value: **32vp**.

Percentage values are not supported.

**Type:** [Length](../arkts-apis/arkts-arkui-length-t.md)

**Default:** When isSidebarMiddle is false, the default value is 24vp, Otherwise,the default value is 32vp

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## isSidebarMiddle

```TypeScript
isSidebarMiddle?: boolean
```

Whether the arrow is centered on both sides of the **Swiper** component. The value **true** means that the arrow is centered on both sides of the **Swiper** component, and **false** means that the arrow is show on either side of the navigation indicator.

Default value: **false**.

**Type:** boolean

**Default:** false

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## showBackground

```TypeScript
showBackground?: boolean
```

Whether to show the background for the arrow. The value **true** means to show the background for the arrow, and **false** means the opposite.

Default value: **false**.

**Type:** boolean

**Default:** false

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
