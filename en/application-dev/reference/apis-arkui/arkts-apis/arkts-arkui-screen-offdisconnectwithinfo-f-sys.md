# offDisconnectWithInfo (System API)

## Modules to Import

```TypeScript
import { screen } from '@kit.ArkUI';
```

## offDisconnectWithInfo

```TypeScript
function offDisconnectWithInfo(callback?: Callback<ScreenDisconnectInfo>): void
```

Unsubscribes from screen disconnect events.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-screen-function offDisconnectWithInfo(callback?: Callback<ScreenDisconnectInfo>): void--><!--Device-screen-function offDisconnectWithInfo(callback?: Callback<ScreenDisconnectInfo>): void-End-->

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[ScreenDisconnectInfo](arkts-arkui-screen-screendisconnectinfo-i-sys.md)&gt; | No | Callback used to return the screen disconnect information, including the screen ID and disconnection reason. If not provided, all callbacks for the given event type will be removed. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
