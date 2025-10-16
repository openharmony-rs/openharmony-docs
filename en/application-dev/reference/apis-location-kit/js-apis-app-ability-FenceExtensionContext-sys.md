# @ohos.app.ability.FenceExtensionContext (FenceExtensionContext) (System API)
<!--Kit: Location Kit-->
<!--Subsystem: Location-->
<!--Owner: @liu-binjun-->
<!--Designer: @liu-binjun-->
<!--Tester: @mhy123456789-->
<!--Adviser: @RayShih-->

The **FenceExtensionContext** class defines the context for **FenceExtensionAbility** objects. Inherited from [ExtensionContext](../apis-ability-kit/js-apis-inner-application-extensionContext.md), this class provides the configuration information of **FenceExtensionAbility** objects and the API for starting them.

> **NOTE**
>
> The initial APIs of this module are supported since API version 14. Newly added APIs will be marked with a superscript to indicate their earliest API version. 
> The APIs of this module can be used only in the stage model. 
> The APIs provided by this module are system APIs.

## Modules to Import

```ts
import { FenceExtensionContext } from '@kit.LocationKit';
```

## Usage

Before using **FenceExtensionContext**, you must first obtain a **FenceExtensionAbility** instance.

```ts
import { FenceExtensionAbility, FenceExtensionContext } from '@kit.LocationKit';

class MyFenceExtensionAbility extends FenceExtensionAbility {
  onCreate() {
    let fenceExtensionContext: FenceExtensionContext = this.context;
  }
}
```

## FenceExtensionContext.startAbility

startAbility(want: Want): Promise&lt;void&gt;

Starts an ability. This API uses a promise to return the result. It can be called only by the main thread.

**System API**: This is a system API.

**System capability**: SystemCapability.Location.Location.Geofence

**Parameters**

| Name|                Type              | Mandatory|              Description              |
| ------| --------------------------------- | ---- | -------------------------------------- |
| want| [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes | 	Want information about the target ability.|

**Returns**

| Type         | Description                               |
| ------------ | ---------------------------------- |
| Promise&lt;void&gt; | Promise used to return the result.|

**Error codes**

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 202     | The application is not system-app, can not use system-api.      |
| 401     | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.      |
| 16000001 | The specified ability does not exist.                        |
| 16000002 | Incorrect ability type.                                      |
| 16000004 | Cannot start an invisible component.                         |
| 16000005 | The specified process does not have the permission.          |
| 16000006 | Cross-user operations are not allowed.                       |
| 16000008 | The crowdtesting application expires.                        |
| 16000011 | The context does not exist.                                  |
| 16000012 | The application is controlled.                               |
| 16000013 | The application is controlled by EDM.                        |
| 16000019 | No matching ability is found.                                |
| 16000050 | Internal error.                                              |
| 16200001 | The caller has been released.                                |

For details about the error codes, see [Ability Error Codes](../apis-ability-kit/errorcode-ability.md).

**Example**

```ts
import { FenceExtensionAbility, geoLocationManager } from '@kit.LocationKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { Want } from '@kit.AbilityKit';

export class MyFenceExtensionAbility extends FenceExtensionAbility {
  onFenceStatusChange(transition: geoLocationManager.GeofenceTransition, additions: Record<string, string>): void {
    // Receive the geofence status change event and process the service logic.
    console.info(`on geofence transition,id:${transition.geofenceId},event:${transition.transitionEvent},additions:${JSON.stringify(additions)}`);
    let want: Want = {
      bundleName: "com.example.myapp",
      abilityName: "MyServiceExtensionAbility"
    };
    try {
      this.context.startAbility(want)
        .then(() => {
          // Carry out normal service processing.
          console.info('startAbility succeed');
        })
        .catch((error: BusinessError) => {
          // Process service logic errors.
          console.error('startAbility failed, error.code: ' + JSON.stringify(error.code) +
            ' error.message: ' + JSON.stringify(error.message));
        });
    } catch (paramError) {
      // Process input parameter errors.
      let code = (paramError as BusinessError).code;
      let message = (paramError as BusinessError).message;
      console.error('startAbility failed, error.code: ' + JSON.stringify(code) +
        ' error.message: ' + JSON.stringify(message));
    }
  }
}
```
