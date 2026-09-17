# EllipsisMode

Enumerates the ellipsis styles.

**EllipsisMode.START** and **EllipsisMode.MIDDLE** take effect only when text overflows in a single line.

**Since:** 12

**System capability:** SystemCapability.Graphics.Drawing

## START

```TypeScript
START = 0
```

Ellipsis at the beginning. This enumerated value is valid only when **maxLines** is set to **1** in [ParagraphStyle](arkts-arkgraphics2d-text-paragraphstyle-i.md).

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

## MIDDLE

```TypeScript
MIDDLE = 1
```

Ellipsis in the middle. This enumerated value is valid only when **maxLines** is set to **1** in [ParagraphStyle](arkts-arkgraphics2d-text-paragraphstyle-i.md).

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

## END

```TypeScript
END = 2
```

Ellipsis at the end. This enumerated value is valid when **maxLines** is set to any value in [ParagraphStyle](arkts-arkgraphics2d-text-paragraphstyle-i.md).

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

## MULTILINE_START

```TypeScript
MULTILINE_START = 3
```

Ellipsis at the beginning. This enumerated value is valid when **maxLines** is set to any value in [ParagraphStyle](arkts-arkgraphics2d-text-paragraphstyle-i.md).

**Since:** 24

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.Graphics.Drawing

## MULTILINE_MIDDLE

```TypeScript
MULTILINE_MIDDLE = 4
```

Ellipsis in the middle. This enumerated value is valid when **maxLines** is set to any value in [ParagraphStyle](arkts-arkgraphics2d-text-paragraphstyle-i.md).

**Since:** 24

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.Graphics.Drawing
