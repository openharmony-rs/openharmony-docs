# PixelMapFormat (System API)

Enumerates pixel map formats.

@enum { int }

**Since:** 14

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## NV21

```TypeScript
NV21 = 2
```

Indicates that the storage order is to store Y first and then V U alternately each occupies 8 bits and are stored from the higher-order to the lower-order bits.

**Since:** 14

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## RGBA_8888

```TypeScript
RGBA_8888 = 1
```

Indicates that each pixel is stored on 32 bits. Each pixel contains 4 components：B(8bits), G(8bits), R(8bits), A(8bits) and are stored from the higher-order to the lower-order bits.

**Since:** 14

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## UNKNOWN

```TypeScript
UNKNOWN = 0
```

Indicates an unknown format.

**Since:** 14

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.
