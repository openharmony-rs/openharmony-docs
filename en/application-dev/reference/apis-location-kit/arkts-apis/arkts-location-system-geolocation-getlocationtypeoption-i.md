# GetLocationTypeOption

**Since:** 3

**Deprecated since:** 9

**System capability:** SystemCapability.Location.Location.Lite

## Modules to Import

```TypeScript
import { Geolocation, GeolocationResponse, GetLocationOption, GetLocationTypeOption, GetLocationTypeResponse, SubscribeLocationOption } from '@kit.LocationKit';
```

## complete

```TypeScript
complete?: () => void
```

Called when the execution is completed.

**Since:** 3

**Deprecated since:** 9

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Location.Location.Lite

## fail

```TypeScript
fail?: (data: string, code: number) => void
```

Called when the location types fail to be obtained.

**Since:** 3

**Deprecated since:** 9

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Location.Location.Lite

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| data | string | Yes |  |
| code | number | Yes |  |

## success

```TypeScript
success?: (data: GetLocationTypeResponse) => void
```

Called when the location types are obtained.

**Since:** 3

**Deprecated since:** 9

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Location.Location.Lite

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| data | [GetLocationTypeResponse](arkts-location-system-geolocation-getlocationtyperesponse-i.md) | Yes |  |
