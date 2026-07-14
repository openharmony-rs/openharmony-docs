# hasWindowFocus

## hasWindowFocus

```TypeScript
function hasWindowFocus(callback: AsyncCallback<boolean>): void
```

检查Ability的主窗口是否具有窗口焦点。使用callback异步回调。

**起始版本：** 7

**模型约束：** 此接口仅可在FA模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.FAModel

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;boolean&gt; | 是 | 回调函数。<br>如果此Ability当前具有视窗焦点，则返回true；否则返回false。 |

**示例：**

```TypeScript
import { featureAbility } from '@kit.AbilityKit';

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

**系统能力：** SystemCapability.Ability.AbilityRuntime.FAModel

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象。如果此Ability当前具有视窗焦点，则返回true；否则返回false。 |

**示例：**

```TypeScript
import { featureAbility } from '@kit.AbilityKit';

featureAbility.hasWindowFocus().then((data) => {
  console.info(`hasWindowFocus data: ${JSON.stringify(data)}`);
});

```

