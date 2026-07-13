# setDefaultResourceUsageObserver

## setDefaultResourceUsageObserver

```TypeScript
function setDefaultResourceUsageObserver(defaultObserver?: ResourceUsageObserver): ResourceUsageObserver
```

设置资源占用观察者，应用资源超基线时，支持链式回调，返回上一次注册的资源占用观察者，仅限主线程调用。

如果传入非法参数或在子线程调用，将抛出错误码并返回undefined，因此建议使用try-catch逻辑进行处理。

若接口参数为空，后续注册的观察者将无法与前序已注册的观察者建立关联，从而中断链式调用。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本24开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| defaultObserver | ResourceUsageObserver | 否 | 新注册的资源观察者，默认值为空。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ResourceUsageObserver | 返回上一次注册的资源观察者。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16000205](../errorcode-ability.md#16000205-当前接口未在主线程中调用) | API未在主线程中调用。 |

**示例：**

```TypeScript
import { errorManager } from '@kit.AbilityKit';
import { process } from '@kit.ArkTS';

let oldObserver: errorManager.ResourceUsageObserver;
const resourceUsageObserver: errorManager.ResourceUsageObserver = (resourceType, resourceSize, detailInfo) => {
  // 自定义的resourceUsageObserver实现逻辑
  console.info('[Observer] Resource usage observer.');
  if (oldObserver) {
    oldObserver(resourceType, resourceSize, detailInfo);
  } else {
    // 建议增加判空操作，如果为空采用同步退出方式
    const processManager = new process.ProcessManager();
    processManager.exit(0);
  }
};
oldObserver = errorManager.setDefaultResourceUsageObserver(resourceUsageObserver);

```

