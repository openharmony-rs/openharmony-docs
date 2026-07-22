# getAppPreloadType

## 导入模块

```TypeScript
import { application } from '@kit.AbilityKit';
```

## getAppPreloadType

```TypeScript
export function getAppPreloadType(): AppPreloadType
```

获取应用当前进程的预加载类型。
> **说明：**  
>  
> - 只有在进程首次执行[AbilityStage.onCreate](arkts-ability-app-ability-abilitystage-abilitystage-c.md#oncreate)完成之前调用该接口，才可以返回真实的预  
> 加载类型。  
>  
> - AbilityStage创建完成后，应用的预加载数据将被清除，调用该接口将返回UNSPECIFIED，无法获取到真实的预加载类型。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-application-export function getAppPreloadType(): AppPreloadType--><!--Device-application-export function getAppPreloadType(): AppPreloadType-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [AppPreloadType](arkts-ability-application-apppreloadtype-e.md) | 应用当前进程的预加载类型。 |

**示例：**

```TypeScript
import { AbilityStage, application } from '@kit.AbilityKit';

export default class MyAbilityStage extends AbilityStage{
  onCreate() {
    let appPreloadType = application.getAppPreloadType();
  }
}

```

