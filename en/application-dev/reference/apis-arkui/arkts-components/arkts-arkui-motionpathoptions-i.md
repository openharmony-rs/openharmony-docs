# MotionPathOptions

Defines motion path configuration options of the component.

**Since:** 7

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## from

```TypeScript
from?: number
```

Start point of the motion path.

Default value: **0.0**

Value range: [0.0, 1.0].

Values less than 0.0 or greater than 1.0 are treated as the default value 0.0.

**Type:** number

**Default:** 0.0

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## path

```TypeScript
path: string
```

Motion path of the translation animation. The [svg path string](../../../reference/apis-arkui/arkui-ts/ts-drawing-components-path.md#svg-path-syntax) is used. In the value, **start** and **end** can be used in place of the start point and end point, for example, **'Mstart.x start.y L50 50 Lend.x end.y Z'**. For details, see [Path Drawing](../../../ui/ui-js-components-svg-path.md).

If this parameter is set to an empty string, the path animation is not set.

**Type:** string

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## rotatable

```TypeScript
rotatable?: boolean
```

Whether to rotate along the path. The value **true** means to rotate along the path, and **false** means the opposite.

Default value: **false**

**Type:** boolean

**Default:** false

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## to

```TypeScript
to?: number
```

End point of the motion path.

Default value: **1.0**

Value range: [0.0, 1.0].

Values less than 0.0 or greater than 1.0 are treated as the default value 1.0. After this normalization, the **to** value must be greater than or equal to the **from** value.

**Type:** number

**Default:** 1.0

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
