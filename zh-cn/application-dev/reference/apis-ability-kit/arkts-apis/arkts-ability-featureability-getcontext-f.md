# getContext

## getContext

```TypeScript
function getContext(): Context
```

获取应用上下文。

**起始版本：** 6

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为6。

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-featureAbility-function getContext(): Context--><!--Device-featureAbility-function getContext(): Context-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.FAModel

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 返回应用程序上下文。 |

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

