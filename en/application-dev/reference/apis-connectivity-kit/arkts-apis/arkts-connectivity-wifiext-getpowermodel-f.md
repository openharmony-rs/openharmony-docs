# getPowerModel

## Modules to Import

```TypeScript
import { wifiext } from '@kit.ConnectivityKit';
```

## getPowerModel

```TypeScript
function getPowerModel(): Promise<PowerModel>
```

Obtains the current power model. This API uses a promise to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [getPowerMode](arkts-connectivity-wifimanagerext-getpowermode-f.md)

**Required permissions:** ohos.permission.GET_WIFI_INFO

<!--Device-wifiext-function getPowerModel(): Promise<PowerModel>--><!--Device-wifiext-function getPowerModel(): Promise<PowerModel>-End-->

**System capability:** SystemCapability.Communication.WiFi.AP.Extension

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[PowerModel](arkts-connectivity-wifiext-powermodel-e.md)&gt; | Promise used to return the current power model obtained. |


## getPowerModel

```TypeScript
function getPowerModel(callback: AsyncCallback<PowerModel>): void
```

Obtains the current power model. This API uses an asynchronous callback to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [getPowerMode](arkts-connectivity-wifimanagerext-getpowermode-f.md)

**Required permissions:** ohos.permission.GET_WIFI_INFO

<!--Device-wifiext-function getPowerModel(callback: AsyncCallback<PowerModel>): void--><!--Device-wifiext-function getPowerModel(callback: AsyncCallback<PowerModel>): void-End-->

**System capability:** SystemCapability.Communication.WiFi.AP.Extension

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[PowerModel](arkts-connectivity-wifiext-powermodel-e.md)&gt; | Yes | Callback used to return the result. |
