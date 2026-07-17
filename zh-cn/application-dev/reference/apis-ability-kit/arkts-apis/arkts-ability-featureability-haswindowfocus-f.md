# hasWindowFocus

## 导入模块

```TypeScript
import { featureAbility } from '@kit.AbilityKit';
```

## hasWindowFocus

```TypeScript
function hasWindowFocus(callback: AsyncCallback<boolean>): void
```

检查Ability的主窗口是否具有窗口焦点。使用callback异步回调。

**起始版本：** 7

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-featureAbility-function hasWindowFocus(callback: AsyncCallback<boolean>): void--><!--Device-featureAbility-function hasWindowFocus(callback: AsyncCallback<boolean>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.FAModel

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<boolean> | 是 | 回调函数。<br>如果此Ability当前具有视窗焦点，则返回true；否则返回false。 |

**示例：**

```TypeScript
import { featureAbility } from '@kit.AbilityKit';

// 检查Ability的主窗口是否具有窗口焦点
featureAbility.hasWindowFocus((error, data) => {
  if (error && error.code !== 0) {
    console.error(`hasWindowFocus fail, error: ${JSON.stringify(error)}`);
  } else {
    console.info(`hasWindowFocus success, data: ${JSON.stringify(data)}`);
  }
});

```


## hasWindowFocus

```TypeScript
function hasWindowFocus(): Promise<boolean>
```

检查Ability的主窗口是否具有窗口焦点。使用Promise异步回调。

**起始版本：** 7

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-featureAbility-function hasWindowFocus(): Promise<boolean>--><!--Device-featureAbility-function hasWindowFocus(): Promise<boolean>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.FAModel

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<boolean> | Promise对象。如果此Ability当前具有视窗焦点，则返回true；否则返回false。 |

**示例：**

```TypeScript
import { featureAbility } from '@kit.AbilityKit';

// 检查Ability的主窗口是否具有窗口焦点
featureAbility.hasWindowFocus().then((data) => {
  console.info(`hasWindowFocus data: ${JSON.stringify(data)}`);
});

```

