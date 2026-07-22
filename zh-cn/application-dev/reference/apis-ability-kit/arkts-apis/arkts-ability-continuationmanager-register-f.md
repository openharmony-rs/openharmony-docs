# register

## 导入模块

```TypeScript
import { continuationManager } from '@kit.AbilityKit';
```

## register

```TypeScript
function register(callback: AsyncCallback<number>): void
```

注册流转管理服务，并获取对应的注册token，无过滤条件，使用AsyncCallback方式作为异步方法。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** on(type:

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-continuationManager-function register(callback: AsyncCallback<number>): void--><!--Device-continuationManager-function register(callback: AsyncCallback<number>): void-End-->

**系统能力：** SystemCapability.Ability.DistributedAbilityManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | 是 | AsyncCallback形式返回流转管理服务连接后生成的token。 |

**示例：**

```TypeScript
import { continuationManager } from '@kit.AbilityKit';

let token: number = -1;
continuationManager.register((err, data) => {
  if (err.code != 0) {
    console.error('register failed, cause: ' + JSON.stringify(err));
    return;
  }
  console.info('register finished, ' + JSON.stringify(data));
  token = data;
});

```


## register

```TypeScript
function register(options: ContinuationExtraParams, callback: AsyncCallback<number>): void
```

连接流转管理服务，并获取对应的注册token，使用AsyncCallback方式作为异步方法。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** on(type:

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-continuationManager-function register(options: ContinuationExtraParams, callback: AsyncCallback<number>): void--><!--Device-continuationManager-function register(options: ContinuationExtraParams, callback: AsyncCallback<number>): void-End-->

**系统能力：** SystemCapability.Ability.DistributedAbilityManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [ContinuationExtraParams](arkts-ability-continuationextraparams-continuationextraparams-i.md) | 是 | 过滤可选择设备列表的额外参数。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | 是 | AsyncCallback形式返回流转管理服务连接后生成的token。 |

**示例：**

```TypeScript
import { continuationManager } from '@kit.AbilityKit';

let token: number = -1;
continuationManager.register(
  {
    deviceType: ["00E"]
  },
  (err, data) => {
    if (err.code != 0) {
      console.error('register failed, cause: ' + JSON.stringify(err));
      return;
    }
    console.info('register finished, ' + JSON.stringify(data));
    token = data;
});

```


## register

```TypeScript
function register(options?: ContinuationExtraParams): Promise<number>
```

连接流转管理服务，并获取对应的注册token，使用Promise方式作为异步方法。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** on(type:

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-continuationManager-function register(options?: ContinuationExtraParams): Promise<number>--><!--Device-continuationManager-function register(options?: ContinuationExtraParams): Promise<number>-End-->

**系统能力：** SystemCapability.Ability.DistributedAbilityManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [ContinuationExtraParams](arkts-ability-continuationextraparams-continuationextraparams-i.md) | 否 | 过滤可选择设备列表的额外参数，该参数可缺省。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise形式返回流转管理服务连接后生成的token。 |

**示例：**

```TypeScript
import { continuationManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let token: number = -1;
continuationManager.register(
  { deviceType: ["00E"] }).then((data) => {
    console.info('register finished, ' + JSON.stringify(data));
    token = data;
  }).catch((err: BusinessError) => {
    console.error('register failed, cause: ' + JSON.stringify(err));
});

```

