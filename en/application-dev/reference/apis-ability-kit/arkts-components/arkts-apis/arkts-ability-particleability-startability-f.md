# startAbility

## Modules to Import

```TypeScript
import { particleAbility } from '@kit.AbilityKit';
```

## startAbility

```TypeScript
function startAbility(parameter: StartAbilityParameter, callback: AsyncCallback<void>): void
```

Starts a ParticleAbility. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> For details about the startup rules for the components in the FA model, see
> [Component Startup Rules (FA Model)](../../../application-models/component-startup-rules-fa.md).

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Ability.AbilityRuntime.FAModel

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| parameter | [StartAbilityParameter](arkts-ability-startabilityparameter-startabilityparameter-i.md) | Yes | Ability to start. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the ParticleAbility is started, **err** is **undefined**; otherwise, **err** is an error object. |

**Examples**

```TypeScript
import { particleAbility, wantConstant } from '@kit.AbilityKit';

particleAbility.startAbility(
  {
    want:
    {
      action: 'ohos.want.action.home',
      entities: ['entity.system.home'],
      type: 'MIMETYPE',
      flags: wantConstant.Flags.FLAG_AUTH_READ_URI_PERMISSION,
      deviceId: '',
      bundleName: 'com.example.Data',
      abilityName: 'com.example.Data.EntryAbility',
      uri: ''
    },
  },
  (error, data) => {
    if (error && error.code !== 0) {
      console.error(`startAbility fail, error: ${JSON.stringify(error)}`);
    } else {
      console.info(`startAbility success, data: ${JSON.stringify(data)}`);
    }
  },
);
```


<a id="startability-1"></a>

## startAbility

```TypeScript
function startAbility(parameter: StartAbilityParameter): Promise<void>
```

Starts a ParticleAbility. This API uses a promise to return the result.

> **NOTE:** 
> 
> For details about the startup rules for the components in the FA model, see
> [Component Startup Rules (FA Model)](../../../application-models/component-startup-rules-fa.md).

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Ability.AbilityRuntime.FAModel

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| parameter | [StartAbilityParameter](arkts-ability-startabilityparameter-startabilityparameter-i.md) | Yes | Ability to start. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. Promise that returns no value. |

**Examples**

```TypeScript
import { particleAbility, wantConstant } from '@kit.AbilityKit';

particleAbility.startAbility(
  {
    want:
    {
      action: 'ohos.want.action.home',
      entities: ['entity.system.home'],
      type: 'MIMETYPE',
      flags: wantConstant.Flags.FLAG_AUTH_READ_URI_PERMISSION,
      deviceId: '',
      bundleName: 'com.example.Data',
      abilityName: 'com.example.Data.EntryAbility',
      uri: ''
    },
  },
).then(() => {
  console.info('particleAbility startAbility');
});
```
