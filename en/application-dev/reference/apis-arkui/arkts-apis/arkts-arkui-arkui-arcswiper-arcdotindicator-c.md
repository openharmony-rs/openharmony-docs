# ArcDotIndicator

```TypeScript
export class ArcDotIndicator
```

Describes the properties and behavior of the arc dot navigation indicator.

**Since:** 18

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

## Modules to Import

```TypeScript
import { ArcSwiper, ArcSwiperAttribute, ArcDotIndicator, ArcDirection, ArcSwiperController } from '@kit.ArkUI';
```

## arcDirection

```TypeScript
arcDirection(direction: Optional<ArcDirection>): ArcDotIndicator
```

Sets the direction of the arc navigation indicator.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| direction | [Optional](../arkts-components/arkts-arkui-common-comp-optional-t.md)&lt;[ArcDirection](arkts-arkui-arkui-arcswiper-arcdirection-e.md)&gt; | Yes | Direction of the arc navigation indicator.<br>Default value: **ArcDirection.SIX_CLOCK_DIRECTION** (6 o'clock direction) |

**Return value:**

| Type | Description |
| --- | --- |
| [ArcDotIndicator](arkts-arkui-arkui-arcswiper-arcdotindicator-c.md) | Properties and functionality of the arc navigation indicator. |

## backgroundColor

```TypeScript
backgroundColor(color: Optional<ResourceColor>): ArcDotIndicator
```

Sets the color of the arc navigation indicator when it is long-pressed.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| color | [Optional](../arkts-components/arkts-arkui-common-comp-optional-t.md)&lt;[ResourceColor](arkts-arkui-resourcecolor-t.md)&gt; | Yes | Color of the arc navigation indicator when it is long-pressed.<br> Default value: **'#FF404040'** |

**Return value:**

| Type | Description |
| --- | --- |
| [ArcDotIndicator](arkts-arkui-arkui-arcswiper-arcdotindicator-c.md) | Properties and functionality of the arc navigation indicator. |

## constructor

```TypeScript
constructor()
```

A constructor used to create an **ArcDotIndicator** instance.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

## itemColor

```TypeScript
itemColor(color: Optional<ResourceColor>): ArcDotIndicator
```

Sets the color of the unselected navigation points in the arc navigation indicator.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| color | [Optional](../arkts-components/arkts-arkui-common-comp-optional-t.md)&lt;[ResourceColor](arkts-arkui-resourcecolor-t.md)&gt; | Yes | Color of the unselected navigation points in the arc navigation indicator.<br>Default value: **'#A9FFFFFF'** |

**Return value:**

| Type | Description |
| --- | --- |
| [ArcDotIndicator](arkts-arkui-arkui-arcswiper-arcdotindicator-c.md) | Properties and functionality of the arc navigation indicator. |

## maskColor

```TypeScript
maskColor(color: Optional<LinearGradient>): ArcDotIndicator
```

Sets the mask gradient color of the arc navigation indicator.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| color | [Optional](../arkts-components/arkts-arkui-common-comp-optional-t.md)&lt;LinearGradient&gt; | Yes | Mask gradient color of the arc navigation indicator.<br>Default start color: **'#00000000'**<br>Default end color: **'#FF000000'** |

**Return value:**

| Type | Description |
| --- | --- |
| [ArcDotIndicator](arkts-arkui-arkui-arcswiper-arcdotindicator-c.md) | Properties and functionality of the arc navigation indicator. |

## selectedItemColor

```TypeScript
selectedItemColor(color: Optional<ResourceColor>): ArcDotIndicator
```

Sets the color of the selected navigation point in the arc navigation indicator.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| color | [Optional](../arkts-components/arkts-arkui-common-comp-optional-t.md)&lt;[ResourceColor](arkts-arkui-resourcecolor-t.md)&gt; | Yes | Color of the selected navigation point in the arc navigation indicator.<br>Default value: **#FF5EA1FF** |

**Return value:**

| Type | Description |
| --- | --- |
| [ArcDotIndicator](arkts-arkui-arkui-arcswiper-arcdotindicator-c.md) | Properties and functionality of the arc navigation indicator. |
