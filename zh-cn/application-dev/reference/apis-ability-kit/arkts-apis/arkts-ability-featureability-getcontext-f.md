# getContext

## 导入模块

```TypeScript
import { featureAbility } from '@kit.AbilityKit';
```

<a id="getcontext"></a>
## getContext

```TypeScript
function getContext(): Context
```

获取应用上下文。

**起始版本：** 6

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-featureAbility-function getContext(): Context--><!--Device-featureAbility-function getContext(): Context-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.FAModel

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Context](../../apis-arkui/arkts-components/arkts-arkui-context-t.md) | 返回应用程序上下文。 |

**示例：**

```TypeScript
import { featureAbility } from '@kit.AbilityKit';

// 获取应用上下文
let context = featureAbility.getContext();
context.getBundleName((error, data) => {
  if (error && error.code !== 0) {
    console.error(`getBundleName fail, error: ${JSON.stringify(error)}`);
  } else {
    console.info(`getBundleName success, data: ${JSON.stringify(data)}`);
  }
});

```

