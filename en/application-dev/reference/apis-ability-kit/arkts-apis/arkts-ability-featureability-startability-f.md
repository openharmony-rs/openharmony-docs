# startAbility

## Modules to Import

```TypeScript
import { featureAbility } from '@kit.AbilityKit';
```

## startAbility

```TypeScript
function startAbility(parameter: StartAbilityParameter, callback: AsyncCallback<number>): void
```

Starts an ability. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> For details about the startup rules for the components in the FA model, see
> [Component Startup Rules (FA Model)](../../../application-models/component-startup-rules-fa.md).

**Since:** 6

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Ability.AbilityRuntime.FAModel

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| parameter | [StartAbilityParameter](arkts-ability-startabilityparameter-startabilityparameter-i.md) | Yes | Ability to start. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined** and **data** is **0**; otherwise, **err** is a non-zero value. |

**Examples**

```TypeScript
import { featureAbility, wantConstant } from '@kit.AbilityKit';

// Start a new Ability.
featureAbility.startAbility(
  {
    want:
    {
      action: '',
      entities: [''],
      type: '',
      flags: wantConstant.Flags.FLAG_AUTH_READ_URI_PERMISSION,
      deviceId: '',
      bundleName: 'com.example.myapplication',
      /* In the FA model, abilityName consists of package and ability names. */
      abilityName: 'com.example.myapplication.secondAbility',
      uri: ''
    },
  },
  (error, data) => {
    if (error && error.code !== 0) {
      console.error(`startAbility fail, error: ${JSON.stringify(error)}`);
    } else {
      console.info(`startAbility success, data: ${JSON.stringify(data)}`);
    }
  }
);
```


<a id="startability-1"></a>

## startAbility

```TypeScript
function startAbility(parameter: StartAbilityParameter): Promise<number>
```

Starts an ability. This API uses a promise to return the result.

> **NOTE:** 
> 
> For details about the startup rules for the components in the FA model, see
> [Component Startup Rules (FA Model)](../../../application-models/component-startup-rules-fa.md).

**Since:** 6

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Ability.AbilityRuntime.FAModel

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| parameter | [StartAbilityParameter](arkts-ability-startabilityparameter-startabilityparameter-i.md) | Yes | Ability to start. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise used to return the result. If the operation is successful, **0** is returned; otherwise, a non-zero value is returned. |

**Examples**

```TypeScript
import { featureAbility, wantConstant } from '@kit.AbilityKit';

// Start a new Ability.
featureAbility.startAbility(
  {
    want:
    {
      action: 'ohos.want.action.home',
      entities: ['entity.system.home'],
      type: 'MIMETYPE',
      flags: wantConstant.Flags.FLAG_AUTH_READ_URI_PERMISSION,
      deviceId: '',
      bundleName: 'com.example.myapplication',
      /* In the FA model, abilityName consists of package and ability names. */
      abilityName: 'com.example.myapplication.secondAbility',
      uri: ''
    },
  }
).then((data) => {
  console.info(`startAbility data: ${JSON.stringify(data)}`);
});
```
