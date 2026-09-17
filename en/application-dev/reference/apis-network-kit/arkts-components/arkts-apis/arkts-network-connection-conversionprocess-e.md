# ConversionProcess

Enumerates the parameters of the ASCII/Unicode transcoding process.

**Since:** 23

**System capability:** SystemCapability.Communication.NetManager.Core

## NO_CONFIGURATION

```TypeScript
NO_CONFIGURATION = 0
```

Only domain names with assigned Unicode code points can be converted. (Unicode assigns a unique number to each character. This number is called a code point.)

**Since:** 23

**System capability:** SystemCapability.Communication.NetManager.Core

## ALLOW_UNASSIGNED

```TypeScript
ALLOW_UNASSIGNED = 1
```

Allows the translation of domain names that contain unassigned Unicode code points (in a Unicode character set, not all code points are assigned characters, i.e., unassigned Unicode code points).

**Since:** 23

**System capability:** SystemCapability.Communication.NetManager.Core

## USE_STD3_ASCII_RULES

```TypeScript
USE_STD3_ASCII_RULES = 2
```

During the conversion, the STD-3 ASCII rule (RFC 1123 standard) is forcibly used to check the generated ASCII domain name.

**Since:** 23

**System capability:** SystemCapability.Communication.NetManager.Core
