# startAbilityForResult

## 导入模块

```TypeScript
import { featureAbility } from '@kit.AbilityKit';
```

## startAbilityForResult

```TypeScript
function startAbilityForResult(parameter: StartAbilityParameter, callback: AsyncCallback<AbilityResult>): void
```

启动一个Ability。使用callback异步回调。启动Ability后，存在如下几种情况：

- 正常情况下可通过调用[terminateSelfWithResult](arkts-ability-featureability-terminateselfwithresult-f.md#terminateselfwithresult)接口使之终止并且返回结果给调用方。  
- 异常情况下比如杀死Ability会返回异常信息给调用方, 异常信息中resultCode为-1。  
- 如果被启动的Ability模式是单实例模式, 不同应用多次调用该接口启动这个Ability，当这个Ability调用[terminateSelfWithResult](arkts-ability-featureability-terminateselfwithresult-f.md#terminateselfwithresult)接口使之终止时，只将正常结果返回给最后一个调用方, 其它调用方返回异常信息, 异常信息中resultCode为-1。
> **说明：**  
>  
> 组件启动规则详见：[组件启动规则（FA模型）](../../../application-models/component-startup-rules-fa.md)。

**起始版本：** 7

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-featureAbility-function startAbilityForResult(parameter: StartAbilityParameter, callback: AsyncCallback<AbilityResult>): void--><!--Device-featureAbility-function startAbilityForResult(parameter: StartAbilityParameter, callback: AsyncCallback<AbilityResult>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.FAModel

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| parameter | [StartAbilityParameter](arkts-ability-ability-startabilityparameter-t.md) | 是 | 表示被启动的Ability。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;AbilityResult&gt; | 是 | 回调函数。当启动Ability成功，err为undefined，data为ability的启动结果；否则为错误对象。 |

**示例：**

```TypeScript
import { featureAbility, wantConstant } from '@kit.AbilityKit';

// 启动一个Ability并获取返回结果
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
      /* FA模型中abilityName由package + Ability name组成 */
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


## startAbilityForResult

```TypeScript
function startAbilityForResult(parameter: StartAbilityParameter): Promise<AbilityResult>
```

启动一个Ability。使用Promise异步回调。启动Ability后，存在如下几种情况：

- 正常情况下可通过调用[terminateSelfWithResult](arkts-ability-featureability-terminateselfwithresult-f.md#terminateselfwithresult)接口使之终止并且返回结果给调用方。  
- 异常情况下比如杀死Ability会返回异常信息给调用方, 异常信息中resultCode为-1。  
- 如果被启动的Ability模式是单实例模式, 不同应用多次调用该接口启动这个Ability，当这个Ability调用[terminateSelfWithResult](arkts-ability-featureability-terminateselfwithresult-f.md#terminateselfwithresult)接口使之终止时，只将正常结果返回给最后一个调用方, 其它调用方返回异常信息, 异常信息中resultCode为-1。
> **说明：**  
>  
> 组件启动规则详见：[组件启动规则（FA模型）](../../../application-models/component-startup-rules-fa.md)。

**起始版本：** 7

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-featureAbility-function startAbilityForResult(parameter: StartAbilityParameter): Promise<AbilityResult>--><!--Device-featureAbility-function startAbilityForResult(parameter: StartAbilityParameter): Promise<AbilityResult>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.FAModel

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| parameter | [StartAbilityParameter](arkts-ability-ability-startabilityparameter-t.md) | 是 | 表示被启动的Ability。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;AbilityResult&gt; | Promise对象，返回启动Ability的结果。 |

**示例：**

```TypeScript
import { featureAbility, wantConstant } from '@kit.AbilityKit';

// 启动一个Ability并获取返回结果
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
      /* FA模型中abilityName由package + Ability name组成 */
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

