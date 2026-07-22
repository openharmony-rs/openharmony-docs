# startAbility

## 导入模块

```TypeScript
import { featureAbility } from '@kit.AbilityKit';
```

## startAbility

```TypeScript
function startAbility(parameter: StartAbilityParameter, callback: AsyncCallback<number>): void
```

启动新的Ability。使用callback异步回调。
> **说明：**  
>  
> 组件启动规则详见：[组件启动规则（FA模型）](../../../application-models/component-startup-rules-fa.md)。

**起始版本：** 6

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-featureAbility-function startAbility(parameter: StartAbilityParameter, callback: AsyncCallback<number>): void--><!--Device-featureAbility-function startAbility(parameter: StartAbilityParameter, callback: AsyncCallback<number>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.FAModel

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| parameter | [StartAbilityParameter](arkts-ability-ability-startabilityparameter-t.md) | 是 | 表示被启动的Ability。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | 是 | 回调函数。当启动Ability成功，err为undefined，data为0表示启动成功，data为其他表示启动失败；否则为错误对象。 |

**示例：**

```TypeScript
import { featureAbility, wantConstant } from '@kit.AbilityKit';

// 启动新的Ability
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
      /* FA模型中abilityName由package + Ability name组成 */
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


## startAbility

```TypeScript
function startAbility(parameter: StartAbilityParameter): Promise<number>
```

启动新的Ability。使用Promise异步回调。
> **说明：**  
>  
> 组件启动规则详见：[组件启动规则（FA模型）](../../../application-models/component-startup-rules-fa.md)。

**起始版本：** 6

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-featureAbility-function startAbility(parameter: StartAbilityParameter): Promise<number>--><!--Device-featureAbility-function startAbility(parameter: StartAbilityParameter): Promise<number>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.FAModel

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| parameter | [StartAbilityParameter](arkts-ability-ability-startabilityparameter-t.md) | 是 | 表示被启动的Ability。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise对象。返回0表示启动成功，返回其他表示启动失败。 |

**示例：**

```TypeScript
import { featureAbility, wantConstant } from '@kit.AbilityKit';

// 启动新的Ability
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
      /* FA模型中abilityName由package + Ability name组成 */
      abilityName: 'com.example.myapplication.secondAbility',
      uri: ''
    },
  }
).then((data) => {
  console.info(`startAbility data: ${JSON.stringify(data)}`);
});

```

