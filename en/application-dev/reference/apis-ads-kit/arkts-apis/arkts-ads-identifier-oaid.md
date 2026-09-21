# @ohos.identifier.oaid(OAID)

This module provides the capability of obtaining and resetting the Open Anonymous Device Identifier (OAID).

> **NOTE:** 

> To use the API for obtaining the OAID, you need to
> [request user authorization](../../../security/AccessToken/request-user-authorization.md) (the permission is
> enabled by default): ohos.permission.APP_TRACKING_CONSENT.

**Since:** 10

**System capability:** SystemCapability.Advertising.OAID

## Modules to Import

```TypeScript
import { identifier } from '@kit.AdsKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [getOAID](arkts-ads-identifier-getoaid-f.md#getoaid) | Obtains the OAID. This API uses an asynchronous callback to return the result. |
| [getOAID](arkts-ads-identifier-getoaid-f.md#getoaid-1) | Obtains the OAID. This API uses a promise to return the result. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [resetOAID](arkts-ads-identifier-resetoaid-f-sys.md) | Resets the OAID. |
<!--DelEnd-->
