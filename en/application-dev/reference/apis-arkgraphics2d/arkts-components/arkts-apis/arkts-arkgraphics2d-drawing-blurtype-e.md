# BlurType

```TypeScript
enum BlurType
```

Enumerates the blur types of a mask filter.

| Name | Value| Description | Diagram |  
| ------ | - | ------------------ | -------- |  
| NORMAL | 0 | Both the outer edges and the inner solid parts are blurred.|![image_BlueType_Normal.png](../../../reference/apis-arkgraphics2d/figures/zh-ch_image_BlueType_Normal.png)|

| SOLID | 1 | The inner solid part remains unchanged, while only the outer edges are blurred.|![image_BlueType_Solid.png](../../../reference/apis-arkgraphics2d/figures/zh-ch_image_BlueType_Solid.png)|

| OUTER | 2 | Only the outer edges are blurred, with the inner solid part being fully transparent.|![image_BlueType_Outer.png](../../../reference/apis-arkgraphics2d/figures/zh-ch_image_BlueType_Outer.png)|

| INNER | 3 | Only the inner solid part is blurred, while the outer edges remain sharp.|![image_BlueType_Inner.png](../../../reference/apis-arkgraphics2d/figures/zh-ch_image_BlueType_Inner.png)|

**Since:** 12

**System capability:** SystemCapability.Graphics.Drawing

## NORMAL

```TypeScript
NORMAL = 0
```

Both the outer edges and the inner solid parts are blurred.

**Since:** 12

**System capability:** SystemCapability.Graphics.Drawing

## SOLID

```TypeScript
SOLID = 1
```

The inner solid part remains unchanged, while only the outer edges are blurred.

**Since:** 12

**System capability:** SystemCapability.Graphics.Drawing

## OUTER

```TypeScript
OUTER = 2
```

Only the outer edges are blurred, with the inner solid part being fully transparent.

**Since:** 12

**System capability:** SystemCapability.Graphics.Drawing

## INNER

```TypeScript
INNER = 3
```

Only the inner solid part is blurred, while the outer edges remain sharp.

**Since:** 12

**System capability:** SystemCapability.Graphics.Drawing
