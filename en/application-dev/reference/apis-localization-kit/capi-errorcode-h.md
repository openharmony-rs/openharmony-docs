# errorcode.h

<!--Kit: Localization Kit-->
<!--Subsystem: Global-->
<!--Owner: @yliupy-->
<!--Designer: @zw_feifei-->
<!--Tester: @lpw_work-->
<!--Adviser: @ningningW-->
<!-- md-trans-meta sourceCommit=1a7fdda7cb0bdacc6b1c367c8fd0def17530cd88 translatedAt=2026-11-04T03:47:19.427Z pushedAt=2026-11-04T10:13:14.865Z nl=1 -->

## Overview

Provides the error codes returned by internationalization APIs.

**References**: <i18n/errorcode.h>

**Library**: libohi18n.so

**System capability**: SystemCapability.Global.I18n

**Since**: 22

**Related module**: [i18n](capi-i18n.md)

## Summary

### Enums

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [I18n_ErrorCode](#i18n_errorcode) | I18n_ErrorCode | Internationalization error code.|

## Enum Description

### I18n_ErrorCode

```c
enum I18n_ErrorCode
```

**Description**

Internationalization error code.

**System capability**: SystemCapability.Global.I18n

**Since**: 22

| Value| Description|
| -- | -- |
| SUCCESS = 0 | Success.|
| ERROR_INVALID_PARAMETER = 8900001 | Invalid input parameter.|
| UNEXPECTED_ERROR = 8900050 | Unexpected error, for example, memory error.|


