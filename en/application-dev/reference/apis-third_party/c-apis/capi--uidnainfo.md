# UIDNAInfo

## Overview

Output container for IDNA processing errors.Initialize with UIDNA_INFO_INITIALIZER:\codeUIDNAInfo info = UIDNA_INFO_INITIALIZER;int32_t length = uidna_nameToASCII(..., &info, &errorCode);if(U_SUCCESS(errorCode) && info.errors!=0) { ... }\endcode

## Summary

### Member variables

| Name | Description |
| -- | -- |
| int16_t size | sizeof(UIDNAInfo) @stable ICU 4.6 |
| UBool isTransitionalDifferent;
 UBool reservedB3 | Set to true if transitional and nontransitional processing produce different results. For details see C++ IDNAInfo::isTransitionalDifferent(). |
| [](capi--uidnainfo.md) | < Reserved field, do not use. @internal |
| uint32_t errors;
 int32_t reservedI2 | Bit set indicating IDNA processing errors. 0 if no errors. See UIDNA_ERROR_... constants. |
| int32_t reservedI3 | < Reserved field, do not use. @internal |
| [](capi--uidnainfo.md) | < Reserved field, do not use. @internal |


