# @ohos.wifiext (WLAN Extension)

<!--Kit: Connectivity Kit-->
<!--Subsystem: Communication-->
<!--Owner: @qq_43802146-->
<!--Designer: @qq_43802146-->
<!--Tester: @furryfurry123-->
<!--Adviser: @zhang_yixin13-->
This **wifiext** module provides WLAN extension interfaces for non-universal products.

> **NOTE**
>
> The initial APIs of this module are supported since API version 8. Newly added APIs will be marked with a superscript to indicate their earliest API version.
The APIs described in this document are used only for non-universal products, such as routers.
> The APIs provided by this module are no longer maintained since API version 9. You are advised to use [`@ohos.wifiManagerExt (WLAN Extension)`](js-apis-wifiManagerExt.md).

## Modules to Import

```js
import wifiext from '@ohos.wifiext';
```

## wifiext.enableHotspot<sup>(deprecated)</sup>

enableHotspot(): boolean;

Enables the WLAN hotspot.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [wifiManagerExt.enableHotspot](js-apis-wifiManagerExt.md#wifimanagerextenablehotspotdeprecated) instead.

**Required permissions**: ohos.permission.MANAGE_WIFI_HOTSPOT_EXT

**System capability**: SystemCapability.Communication.WiFi.AP.Extension

**Return value**

  | Type| Description|
  | -------- | -------- |
  | boolean | Returns **true** if the operation is successful; returns **false** otherwise.|


## wifiext.disableHotspot<sup>(deprecated)</sup>

disableHotspot(): boolean;

Disables the WLAN hotspot.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [wifiManagerExt.disableHotspot](js-apis-wifiManagerExt.md#wifimanagerextdisablehotspotdeprecated) instead.

**Required permissions**: ohos.permission.MANAGE_WIFI_HOTSPOT_EXT

**System capability**: SystemCapability.Communication.WiFi.AP.Extension

**Return value**

  | Type| Description|
  | -------- | -------- |
  | boolean | Returns **true** if the operation is successful; returns **false** otherwise.|


## wifiext.getSupportedPowerModel<sup>(deprecated)</sup>

getSupportedPowerModel(): Promise&lt;Array&lt;PowerModel&gt;&gt;

Obtains the supported power models. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [wifiManagerExt.getSupportedPowerModel](js-apis-wifiManagerExt.md#wifimanagerextgetsupportedpowermode) instead.

**Required permissions**: ohos.permission.GET_WIFI_INFO

**System capability**: SystemCapability.Communication.WiFi.AP.Extension

**Return value**

  | Type| Description|
  | -------- | -------- |
  | Promise&lt;Array&lt;[PowerModel](#powermodel)&gt;&gt; | Promise used to return the power models obtained.|


## PowerModel

Enumerates the power models.

**System capability**: SystemCapability.Communication.WiFi.AP.Extension

| Name| Value| Description|
| -------- | -------- | -------- |
| SLEEPING | 0 | Sleeping|
| GENERAL | 1 | General|
| THROUGH_WALL | 2 | Through_wall|


## wifiext.getSupportedPowerModel

getSupportedPowerModel(callback: AsyncCallback&lt;Array&lt;PowerModel&gt;&gt;): void

Obtains the supported power models. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.GET_WIFI_INFO

**System capability**: SystemCapability.Communication.WiFi.AP.Extension

**Parameters**

  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | callback | AsyncCallback&lt;Array&lt;[PowerModel](#powermodel)&gt;&gt; | Yes| Callback used to return the result. If the operation is successful, **err** is **0** and **data** is the power models obtained. If the operation fails, **err** is not **0**.|


## wifiext.getPowerModel<sup>(deprecated)</sup>

getPowerModel(): Promise&lt;PowerModel&gt;

Obtains the power model. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [wifiManagerExt.getSupportedPowerModel](js-apis-wifiManagerExt.md#wifimanagerextgetpowermode) instead.

**Required permissions**: ohos.permission.GET_WIFI_INFO

**System capability**: SystemCapability.Communication.WiFi.AP.Extension

**Return value**

  | Type| Description|
  | -------- | -------- |
  | Promise&lt;[PowerModel](#powermodel)&gt; | Promise used to return the power models obtained.|


## wifiext.getPowerModel<sup>(deprecated)</sup>

getPowerModel(callback: AsyncCallback&lt;PowerModel&gt;): void

Obtains the power model. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [wifiManagerExt.getSupportedPowerModel](js-apis-wifiManagerExt.md#wifimanagerextgetpowermode-1) instead.

**Required permissions**: ohos.permission.GET_WIFI_INFO

**System capability**: SystemCapability.Communication.WiFi.AP.Extension

**Parameters**

  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | callback | AsyncCallback&lt;[PowerModel](#powermodel)&gt; | Yes| Callback used to return the result. If the operation is successful, **err** is **0** and **data** is the power model obtained. If the operation fails, **err** is not **0**.|


## wifiext.setPowerModel

setPowerModel(model: PowerModel) : boolean;

 Sets the power model.

**Required permissions**: ohos.permission.MANAGE_WIFI_HOTSPOT_EXT

**System capability**: SystemCapability.Communication.WiFi.AP.Extension

**Parameters**

  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | model | [PowerModel](#powermodel) | Yes| Power model to set.|

**Return value**

  | Type| Description|
  | -------- | -------- |
  | boolean | Returns **true** if the operation is successful; returns **false** otherwise.|
