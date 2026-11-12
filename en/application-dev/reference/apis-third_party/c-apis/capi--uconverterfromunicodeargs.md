# UConverterFromUnicodeArgs

## Overview

The structure for the fromUnicode callback function parameter.

<!--Device-typedef struct UConverterFromUnicodeArgs {...} UConverterFromUnicodeArgs--><!--Device-typedef struct UConverterFromUnicodeArgs {...} UConverterFromUnicodeArgs-End-->

## Summary

### Member variables

| Name | Description |
| -- | -- |
| UBool flush | < The size of this struct. @stable ICU 2.0 |
| [UConverter](capi--uconverter.md) *converter | < The internal state of converter will be reset and data flushed if set to true. @stable ICU 2.0 |
| const UChar *source | < Pointer to the converter that is opened and to which this struct is passed as an argument. @stable ICU 2.0 |
| const UChar *sourceLimit | < Pointer to the source source buffer. @stable ICU 2.0 |
| char *target | < Pointer to the limit (end + 1) of source buffer. @stable ICU 2.0 |
| const char *targetLimit | < Pointer to the target buffer. @stable ICU 2.0 |
| int32_t *offsets | < Pointer to the limit (end + 1) of target buffer. @stable ICU 2.0 |
| [](capi-ucnv-err-h.md#) | < Pointer to the buffer that receives the offsets. *offset = blah ; offset++;. @stable ICU 2.0 |
| uint16_t size |  |


