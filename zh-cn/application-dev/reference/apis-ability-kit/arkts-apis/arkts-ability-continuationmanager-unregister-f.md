# unregister

## 导入模块

```TypeScript
import { continuationManager } from '@kit.AbilityKit';
```

## unregister

```TypeScript
function unregister(token: number, callback: AsyncCallback<void>): void
```

解注册流转管理服务，传入注册时获取的token进行解注册，使用AsyncCallback方式作为异步方法。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** off(type:

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-continuationManager-function unregister(token: number, callback: AsyncCallback<void>): void--><!--Device-continuationManager-function unregister(token: number, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Ability.DistributedAbilityManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| token | number | 是 | 注册后的token。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | 回调函数。当解注册成功，err为undefined，否则返回错误对象。 |

**示例：**

```TypeScript
import { continuationManager } from '@kit.AbilityKit';

let token: number = 1;
continuationManager.unregister(token, (err) => {
  if (err.code != 0) {
    console.error('unregister failed, cause: ' + JSON.stringify(err));
    return;
  }
  console.info('unregister finished. ');
});

```


## unregister

```TypeScript
function unregister(token: number): Promise<void>
```

解注册流转管理服务，传入注册时获取的token进行解注册，使用Promise方式作为异步方法。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** off(type:

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-continuationManager-function unregister(token: number): Promise<void>--><!--Device-continuationManager-function unregister(token: number): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.DistributedAbilityManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| token | number | 是 | 注册后的token。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise形式返回接口调用结果。 |

**示例：**

```TypeScript
import { continuationManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let token: number = 1;
continuationManager.unregister(token)
  .then(() => {
    console.info('unregister finished. ');
  }).catch((err: BusinessError) => {
    console.error('unregister failed, cause: ' + JSON.stringify(err));
});

```

