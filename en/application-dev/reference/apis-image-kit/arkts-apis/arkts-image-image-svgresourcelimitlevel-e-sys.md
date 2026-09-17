# SVGResourceLimitLevel (System API)

Enumerates SVG resource limit levels.

Higher level allows using less resources during parsing and rendering an SVG image. System-defined default resource limits are always enforced regardless of the specified level.

**Since:** 26.1.0

**System capability:** SystemCapability.Multimedia.Image.Core

**System API:** This is a system API.

## NONE

```TypeScript
NONE = 0
```

Uses the system-defined default SVG resource limits.

This level does not disable SVG resource protection.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

**System API:** This is a system API.

## LOW

```TypeScript
LOW = 1
```

Uses low-level restrictions which means allowing using more SVG resource budget.

This level is suitable for complex SVG images. System-defined default resource limits are still applied.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

**System API:** This is a system API.

## MEDIUM

```TypeScript
MEDIUM = 2
```

Uses medium-level restrictions which means allowing using moderate SVG resource budget.

This level balances SVG compatibility and resource consumption and is suitable for most SVG images.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

**System API:** This is a system API.

## HIGH

```TypeScript
HIGH = 3
```

Uses high-level restrictions which means allowing using less SVG resource budget.

This level is suitable for simple SVG images, such as icons and basic UI resources.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

**System API:** This is a system API.
