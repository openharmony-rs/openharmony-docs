# SystemFontType

Enumerates the font types, which can be combined through bitwise OR operations.

**Since:** 14

**System capability:** SystemCapability.Graphics.Drawing

## ALL

```TypeScript
ALL = 1 << 0
```

All font types, including the system font type, style font type, and user-installed font type.

**Since:** 14

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

## GENERIC

```TypeScript
GENERIC = 1 << 1
```

System font type.

**Since:** 14

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

## STYLISH

```TypeScript
STYLISH = 1 << 2
```

Style font type. The style font type is designed for 2-in-1 devices.

**Since:** 14

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

## INSTALLED

```TypeScript
INSTALLED = 1 << 3
```

Font type that has been installed.

**Since:** 14

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

## CUSTOMIZED

```TypeScript
CUSTOMIZED = 1 << 4
```

Custom font type.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing
