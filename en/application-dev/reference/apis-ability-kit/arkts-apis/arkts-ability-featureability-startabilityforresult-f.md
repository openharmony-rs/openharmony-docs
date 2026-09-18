# startAbilityForResult

## Modules to Import

```TypeScript
import { featureAbility } from '@kit.AbilityKit';
```

## startAbilityForResult

```TypeScript
function startAbilityForResult(parameter: StartAbilityParameter, callback: AsyncCallback<AbilityResult>): void
```

Starts an ability. This API uses an asynchronous callback to return the result. The following situations may be possible for a started ability:

- Normally, you can call [terminateSelfWithResult](arkts-ability-featureability-terminateselfwithresult-f.md) to terminate the ability. The result is returned to the caller.  
- If an exception occurs, for example, the ability is killed, an exception message, in which **resultCode** is  
**-1**, is returned to the caller.  
- If different applications call this API to start an ability that uses the singleton mode and then call [terminateSelfWithResult](arkts-ability-featureability-terminateselfwithresult-f.md) to terminate the ability, the normal result is returned to the last caller, and an exception message, in which **resultCode** is **-1**, is returned to others.

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
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[AbilityResult](arkts-ability-abilityresult-abilityresult-i.md)&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined** and **data** is an AbilityResult object; otherwise, err is an error object. |

**Examples**

```TypeScript
import { featureAbility, wantConstant } from '@kit.AbilityKit';

// Start an Ability and obtain the returned result.
featureAbility.startAbilityForResult(
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
  },
  (error, data) => {
    if (error && error.code !== 0) {
      console.error(`startAbilityForResult fail, error: ${JSON.stringify(error)}`);
    } else {
      console.info(`startAbilityForResult success, data: ${JSON.stringify(data)}`);
    }
  }
);
```

```TypeScript
import { featureAbility, wantConstant } from '@kit.AbilityKit';

// Start an Ability and obtain the return result.
featureAbility.startAbilityForResult(
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
      uri: '',
      parameters:
      {
        mykey0: 1111,
        mykey1: [1, 2, 3],
        mykey2: '[1, 2, 3]',
        mykey3: 'xxxxxxxxxxxxxxxxxxxxxx',
        mykey4: [1, 15],
        mykey5: [false, true, false],
        mykey6: ['aaaaaa', 'bbbbb', 'ccccccccccc'],
        mykey7: true,
      },
    },
  },
).then((data) => {
  console.info(`startAbilityForResult data: ${JSON.stringify(data)}`);
});
```


## startAbilityForResult

```TypeScript
function startAbilityForResult(parameter: StartAbilityParameter): Promise<AbilityResult>
```

Starts an ability. This API uses a promise to return the result. The following situations may be possible for a started ability:

- Normally, you can call [terminateSelfWithResult](arkts-ability-featureability-terminateselfwithresult-f.md) to terminate the ability. The result is returned to the caller.  
- If an exception occurs, for example, the ability is killed, an exception message, in which **resultCode** is  
**-1**, is returned to the caller.  
- If different applications call this API to start an ability that uses the singleton mode and then call [terminateSelfWithResult](arkts-ability-featureability-terminateselfwithresult-f.md) to terminate the ability, the normal result is returned to the last caller, and an exception message, in which **resultCode** is **-1**, is returned to others.

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
| Promise&lt;[AbilityResult](arkts-ability-abilityresult-abilityresult-i.md)&gt; | Promise used to return the result. |

**Examples**

See [startAbilityForResult](#startabilityforresult)
