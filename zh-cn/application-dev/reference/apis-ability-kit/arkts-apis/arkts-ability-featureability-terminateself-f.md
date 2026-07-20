# terminateSelf

## 导入模块

```TypeScript
import { featureAbility } from '@kit.AbilityKit';
```

<a id="terminateself"></a>
## terminateSelf

```TypeScript
function terminateSelf(callback: AsyncCallback<void>): void
```

停止当前的Ability。使用callback异步回调。

**起始版本：** 7

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-featureAbility-function terminateSelf(callback: AsyncCallback<void>): void--><!--Device-featureAbility-function terminateSelf(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.FAModel

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当停止当前的Ability成功，err为undefined，否则为错误对象。 |

**示例：**

```TypeScript
import { featureAbility } from '@kit.AbilityKit';

// 停止当前的Ability
featureAbility.terminateSelf(
  (error) => {
    console.error(`error: ${JSON.stringify(error)}`);
  }
)

```


<a id="terminateself-1"></a>
## terminateSelf

```TypeScript
function terminateSelf(): Promise<void>
```

停止当前的Ability。使用Promise异步回调。

**起始版本：** 7

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-featureAbility-function terminateSelf(): Promise<void>--><!--Device-featureAbility-function terminateSelf(): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.FAModel

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**示例：**

```TypeScript
import { featureAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 停止当前的Ability
featureAbility.terminateSelf().then(() => {
  console.info('==========================>terminateSelf=======================>');
}).catch((error: BusinessError) => {
  console.error(`terminateSelf failed, error.code: ${error.code}, error.message: ${error.message}`);
});

```

