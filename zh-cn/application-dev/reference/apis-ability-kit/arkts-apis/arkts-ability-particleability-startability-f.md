# startAbility

## 导入模块

```TypeScript
import { particleAbility } from '@kit.AbilityKit';
```

## startAbility

```TypeScript
function startAbility(parameter: StartAbilityParameter, callback: AsyncCallback<void>): void
```

启动指定的particleAbility。使用callback异步回调。
> **说明：**  
>  
> 组件启动规则详见：[组件启动规则（FA模型）](../../../application-models/component-startup-rules-fa.md)。

**起始版本：** 7

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-particleAbility-function startAbility(parameter: StartAbilityParameter, callback: AsyncCallback<void>): void--><!--Device-particleAbility-function startAbility(parameter: StartAbilityParameter, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.FAModel

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| parameter | [StartAbilityParameter](arkts-ability-ability-startabilityparameter-t.md) | 是 | 表示启动的ability。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当启动指定的particleAbility成功，err为undefined，否则为错误对象。 |

**示例：**

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


## startAbility

```TypeScript
function startAbility(parameter: StartAbilityParameter): Promise<void>
```

启动指定的particleAbility。使用Promise异步回调。
> **说明：**  
>  
> 组件启动规则详见：[组件启动规则（FA模型）](../../../application-models/component-startup-rules-fa.md)。

**起始版本：** 7

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-particleAbility-function startAbility(parameter: StartAbilityParameter): Promise<void>--><!--Device-particleAbility-function startAbility(parameter: StartAbilityParameter): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.FAModel

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| parameter | [StartAbilityParameter](arkts-ability-ability-startabilityparameter-t.md) | 是 | 表示启动的ability。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**示例：**

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

