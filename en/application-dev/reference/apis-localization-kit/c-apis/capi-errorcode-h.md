# errorcode.h

## Overview

Provides the error codes returned by internationalization APIs.

**Library**: libohi18n.so

**System capability**: SystemCapability.Global.I18n

**Since**: 22

**Related module**: [i18n](capi-i18n.md)

## Summary

### Enum

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

**Since**: 22

| Enum item | Description |
| -- | -- |
| SUCCESS = 0 | @error Success |
| ERROR_INVALID_PARAMETER = 8900001 | @error Invalid input parameter |
| UNEXPECTED_ERROR = 8900050 | @error Unexpected error, such as memory error. |


