# getApplicationContextInstance

## 导入模块

```TypeScript
import { application } from '@kit.AbilityKit';
```

<a id="getapplicationcontextinstance"></a>
## getApplicationContextInstance

```TypeScript
export function getApplicationContextInstance(): ApplicationContext
```

获取应用上下文。开发者使用该接口时，无需依赖Context基类。重复调用该接口，将获取同一个ApplicationContext实例。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-application-export function getApplicationContextInstance(): ApplicationContext--><!--Device-application-export function getApplicationContextInstance(): ApplicationContext-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ApplicationContext](arkts-ability-applicationcontext-c.md) | 应用上下文。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. Possible causes: Memory operation error. |

**示例：**

```TypeScript
import { AbilityConstant, UIAbility, application, Want, common } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    try {
      let applicationContext: common.ApplicationContext = application.getApplicationContextInstance();
    } catch (error) {
      let code: number = (error as BusinessError).code;
      let message: string = (error as BusinessError).message;
      console.error(`getApplicationContextInstance failed, error.code: ${code}, error.message: ${message}`);
    }
  }
}

```

