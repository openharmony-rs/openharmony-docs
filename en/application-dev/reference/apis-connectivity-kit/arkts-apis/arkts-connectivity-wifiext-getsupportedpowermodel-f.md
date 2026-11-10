# getSupportedPowerModel

## Modules to Import

```TypeScript
import { wifiext } from '@kit.ConnectivityKit';
```

## getSupportedPowerModel

```TypeScript
function getSupportedPowerModel(): Promise<Array<PowerModel>>
```

Obtains the supported power models. This API uses a promise to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [getSupportedPowerMode](arkts-connectivity-wifimanagerext-getsupportedpowermode-f.md)

**Required permissions:** ohos.permission.GET_WIFI_INFO

<!--Device-wifiext-function getSupportedPowerModel(): Promise<Array<PowerModel>>--><!--Device-wifiext-function getSupportedPowerModel(): Promise<Array<PowerModel>>-End-->

**System capability:** SystemCapability.Communication.WiFi.AP.Extension

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[PowerModel](arkts-connectivity-wifiext-powermodel-e.md)&gt;&gt; | Promise used to return the power models obtained. |


## getSupportedPowerModel

```TypeScript
function getSupportedPowerModel(callback: AsyncCallback<Array<PowerModel>>): void
```

Obtains the supported power models. This API uses an asynchronous callback to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [getSupportedPowerMode](arkts-connectivity-wifimanagerext-getsupportedpowermode-f.md)

**Required permissions:** ohos.permission.GET_WIFI_INFO

<!--Device-wifiext-function getSupportedPowerModel(callback: AsyncCallback<Array<PowerModel>>): void--><!--Device-wifiext-function getSupportedPowerModel(callback: AsyncCallback<Array<PowerModel>>): void-End-->

**System capability:** SystemCapability.Communication.WiFi.AP.Extension

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;[PowerModel](arkts-connectivity-wifiext-powermodel-e.md)&gt;&gt; | Yes | Callback used to return the result. |
