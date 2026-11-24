# UConverterToUnicodeArgs

## Overview

The structure for the toUnicode callback function parameter.

<!--Device-typedef struct UConverterToUnicodeArgs {...} UConverterToUnicodeArgs--><!--Device-typedef struct UConverterToUnicodeArgs {...} UConverterToUnicodeArgs-End-->

## Summary

### Member variables

| Name | Description |
| -- | -- |
| UBool flush | < The size of this struct @stable ICU 2.0<br><!--Device-UBool flush--><!--Device-UBool flush-End--> |
| [UConverter](capi--uconverter.md) *converter | < The internal state of converter will be reset and data flushed if set to true. @stable ICU 2.0<br><!--Device-UConverter *converter--><!--Device-UConverter *converter-End--> |
| const char *source | < Pointer to the converter that is opened and to which this struct is passed as an argument. @stable ICU 2.0<br><!--Device-const char *source--><!--Device-const char *source-End--> |
| const char *sourceLimit | < Pointer to the source source buffer. @stable ICU 2.0<br><!--Device-const char *sourceLimit--><!--Device-const char *sourceLimit-End--> |
| UChar *target | < Pointer to the limit (end + 1) of source buffer. @stable ICU 2.0<br><!--Device-UChar *target--><!--Device-UChar *target-End--> |
| const UChar *targetLimit | < Pointer to the target buffer. @stable ICU 2.0<br><!--Device-const UChar *targetLimit--><!--Device-const UChar *targetLimit-End--> |
| int32_t *offsets | < Pointer to the limit (end + 1) of target buffer. @stable ICU 2.0<br><!--Device-int32_t *offsets--><!--Device-int32_t *offsets-End--> |
| [](capi-ucnv-err-h.md#) | < Pointer to the buffer that receives the offsets. *offset = blah ; offset++;. @stable ICU 2.0<br><!--Device---><!--Device--End--> |
| uint16_t size | <!--Device-uint16_t size--><!--Device-uint16_t size-End--> |


