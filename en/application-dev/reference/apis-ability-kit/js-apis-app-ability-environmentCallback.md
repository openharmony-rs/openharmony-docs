# @ohos.app.ability.EnvironmentCallback (System Environment Change Listener)
<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @zexin_c-->
<!--Designer: @li-weifeng2024-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=b3bc27a342923ac4fafa55153b55c4f3b627330f translatedAt=2026-09-03T10:17:22.086Z pushedAt=2026-09-05T10:47:30.388Z -->

The EnvironmentCallback module provides capabilities to listen for system environment changes.

> **NOTE**
> 
> The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> The APIs of this module can be used only in the stage model.


## Modules to Import

```ts
import { EnvironmentCallback } from '@kit.AbilityKit';
```

## EnvironmentCallback

### onConfigurationUpdated

onConfigurationUpdated(config: Configuration): void

Called when the system environment changes, after [a listener has been registered for such events](js-apis-inner-application-applicationContext.md#applicationcontextonenvironment).

> **NOTE**
> 
> The **onConfigurationUpdated** callback runs in the main thread of the current process. Releasing UI components in this callback may block the main thread tasks. Therefore, you are advised not to release UI components in this callback.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Ability.AbilityRuntime.AbilityCore

**Parameters**

  | Name| Type| Mandatory| Description| 
  | -------- | -------- | -------- | -------- |
  | config | [Configuration](js-apis-app-ability-configuration.md) | Yes| Configuration object after the change.|

**Example**

See [Usage of EnvironmentCallback](#usage-of-environmentcallback).

### onMemoryLevel

onMemoryLevel(level: AbilityConstant.MemoryLevel): void

Called when the system memory changes, after [a listener has been registered for such events](js-apis-inner-application-applicationContext.md#applicationcontextonenvironment).

> **NOTE**
> 
> The **onMemoryLevel** callback runs in the main thread of the current process. Releasing UI components in this callback may block the main thread tasks. Therefore, you are advised not to release UI components in this callback.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Ability.AbilityRuntime.AbilityCore

**Parameters**

  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | level | [AbilityConstant.MemoryLevel](js-apis-app-ability-abilityConstant.md#memorylevel) | Yes | Memory level of the entire device. For the corresponding trigger scenarios, see [AbilityConstant.MemoryLevel](js-apis-app-ability-abilityConstant.md#memorylevel). |

**Example**

See [Usage of EnvironmentCallback](#usage-of-environmentcallback).

## Usage of EnvironmentCallback

**Example**

```ts
import { UIAbility, EnvironmentCallback } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let callbackId: number;

export default class MyAbility extends UIAbility {
  onCreate() {
    console.info('MyAbility onCreate');
    let environmentCallback: EnvironmentCallback  =  {
      onConfigurationUpdated(config){
        console.info(`onConfigurationUpdated config: ${JSON.stringify(config)}`);
      },

      onMemoryLevel(level){
        console.info(`onMemoryLevel level: ${JSON.stringify(level)}`);
      }
    };
    // 1. Obtain an applicationContext object.
    let applicationContext = this.context.getApplicationContext();
    try {
      // 2. Register a listener for system environment changes through applicationContext.
      callbackId = applicationContext.on('environment', environmentCallback);
    } catch (paramError) {
      console.error(`error: ${(paramError as BusinessError).code}, ${(paramError as BusinessError).message}`);
    }
    console.info(`registerEnvironmentCallback number: ${JSON.stringify(callbackId)}`);
  }

  onDestroy() {
    let applicationContext = this.context.getApplicationContext();
    try {
      applicationContext.off('environment', callbackId, (error, data) => {
        if (error && error.code !== 0) {
          console.error(`unregisterEnvironmentCallback fail, error: ${JSON.stringify(error)}`);
        } else {
          console.info(`unregisterEnvironmentCallback success, data: ${JSON.stringify(data)}`);
        }
      });
    } catch (paramError) {
      console.error(`error: ${(paramError as BusinessError).code}, ${(paramError as BusinessError).message}`);
    }
  }
}
```