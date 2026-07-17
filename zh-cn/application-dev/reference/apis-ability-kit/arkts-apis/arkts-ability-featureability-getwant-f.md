# getWant

## 导入模块

```TypeScript
import { featureAbility } from '@kit.AbilityKit';
```

## getWant

```TypeScript
function getWant(callback: AsyncCallback<Want>): void
```

获取要拉起的Ability对应的Want。使用callback异步回调。

**起始版本：** 6

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-featureAbility-function getWant(callback: AsyncCallback<Want>): void--><!--Device-featureAbility-function getWant(callback: AsyncCallback<Want>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.FAModel

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<Want> | 是 | 回调函数，返回want信息。 |

**示例：**

```TypeScript
import { featureAbility } from '@kit.AbilityKit';

// 获取要拉起的Ability对应的Want
featureAbility.getWant((error, data) => {
  if (error && error.code !== 0) {
    console.error(`getWant fail, error: ${JSON.stringify(error)}`);
  } else {
    console.info(`getWant success, data: ${JSON.stringify(data)}`);
  }
});

```


## getWant

```TypeScript
function getWant(): Promise<Want>
```

获取要拉起的Ability对应的Want。使用Promise异步回调。

**起始版本：** 6

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-featureAbility-function getWant(): Promise<Want>--><!--Device-featureAbility-function getWant(): Promise<Want>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.FAModel

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<Want> | Promise对象，返回want信息。 |

**示例：**

```TypeScript
import { featureAbility } from '@kit.AbilityKit';

// 获取要拉起的Ability对应的Want
featureAbility.getWant().then((data) => {
  console.info(`getWant data: ${JSON.stringify(data)}`);
});

```

