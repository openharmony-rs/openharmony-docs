# GetDeviceOptions

```TypeScript
export interface GetDeviceOptions
```

Defines the parameters for obtaining the device information.

**Since:** 3

**Deprecated since:** 6

**System capability:** SystemCapability.Startup.SystemInfo.Lite

## Modules to Import

```TypeScript
import { Device, DeviceResponse, GetDeviceOptions } from '@kit.BasicServicesKit';
```

## complete

```TypeScript
complete?: () => void
```

Callback invoked when the API call is complete (regardless of whether the call is successful or fails). This callback can be used in the cleanup or finalization work. If this parameter is not passed, the callback will not be executed when the API call is complete.

**Since:** 3

**Deprecated since:** 6

**Model restriction:** This API can be used in both the stage model and FA model.

**System capability:** SystemCapability.Startup.SystemInfo.Lite

## fail

```TypeScript
fail?: (data: any, code: number) => void
```

Callback invoked when the API call fails. **data** is the error object or error description string, and **code** is the error code. **code:200**: Certain information cannot be obtained. You are advised to set this callback to handle errors.

**Since:** 3

**Deprecated since:** 6

**Model restriction:** This API can be used in both the stage model and FA model.

**System capability:** SystemCapability.Startup.SystemInfo.Lite

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| data | any | Yes |  |
| code | number | Yes |  |

## success

```TypeScript
success?: (data: DeviceResponse) => void
```

Callback invoked when the API call is successful. **data** is the device information returned. If this parameter is not passed, the device information cannot be obtained. You are advised to set this callback.

**Since:** 3

**Deprecated since:** 6

**Model restriction:** This API can be used in both the stage model and FA model.

**System capability:** SystemCapability.Startup.SystemInfo.Lite

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| data | [DeviceResponse](arkts-basicservices-system-device-deviceresponse-i.md) | Yes |  |
