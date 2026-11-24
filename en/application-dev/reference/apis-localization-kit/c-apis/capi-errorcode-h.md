# errorcode.h

## Overview

Provides the error codes returned by internationalization APIs.

**Library**: libohi18n.so

**System capability**: SystemCapability.Global.I18n

**Since**: 22

**Related module**: [i18n](capi-localization-kit-i18n.md)

## Summary

### Enums

| Name | typedef keyword | Description |
| -- | -- | -- |
| [I18n_ErrorCode](#i18n_errorcode) | I18n_ErrorCode | error codes of i18n |

## Enum type description

### I18n_ErrorCode

```c
enum I18n_ErrorCode
```

**Description**

error codes of i18n

<!--Device-enum I18n_ErrorCode--><!--Device-enum I18n_ErrorCode-End-->

**System capability**: SystemCapability.Global.I18n

**Since**: 22

| Enum item | Description |
| -- | -- |
| SUCCESS = 0 | &nbsp;Success<br><!--Device-SUCCESS = 0--><!--Device-SUCCESS = 0-End--> |
| ERROR_INVALID_PARAMETER = 8900001 | &nbsp;Invalid input parameter<br><!--Device-ERROR_INVALID_PARAMETER = 8900001--><!--Device-ERROR_INVALID_PARAMETER = 8900001-End--> |
| UNEXPECTED_ERROR = 8900050 | &nbsp;Unexpected error, such as memory error.<br><!--Device-UNEXPECTED_ERROR = 8900050--><!--Device-UNEXPECTED_ERROR = 8900050-End--> |


