# UIDNAInfo

## Overview

Output container for IDNA processing errors.Initialize with UIDNA_INFO_INITIALIZER:\codeUIDNAInfo info = UIDNA_INFO_INITIALIZER;int32_t length = uidna_nameToASCII(..., &info, &errorCode);if(U_SUCCESS(errorCode) && info.errors!=0) { ... }\endcode

<!--Device-struct UIDNAInfo {...}--><!--Device-struct UIDNAInfo {...}-End-->

## Summary

### Member variables

| Name | Description |
| -- | -- |
| int16_t size | sizeof(UIDNAInfo) @stable ICU 4.6<br><!--Device-int16_t size--><!--Device-int16_t size-End--> |
| UBool isTransitionalDifferent;
 UBool reservedB3 | Set to true if transitional and nontransitional processing produce different results. For details see C++ IDNAInfo::isTransitionalDifferent().<br><!--Device-UBool isTransitionalDifferent; UBool reservedB3--><!--Device-UBool isTransitionalDifferent; UBool reservedB3-End--> |
| [](capi--uidna.md) | < Reserved field, do not use. @internal<br><!--Device---><!--Device--End--> |
| uint32_t errors;
 int32_t reservedI2 | Bit set indicating IDNA processing errors. 0 if no errors. See UIDNA_ERROR_... constants.<br><!--Device-uint32_t errors; int32_t reservedI2--><!--Device-uint32_t errors; int32_t reservedI2-End--> |
| int32_t reservedI3 | < Reserved field, do not use. @internal<br><!--Device-int32_t reservedI3--><!--Device-int32_t reservedI3-End--> |
| [](capi--uidna.md) | < Reserved field, do not use. @internal<br><!--Device---><!--Device--End--> |


