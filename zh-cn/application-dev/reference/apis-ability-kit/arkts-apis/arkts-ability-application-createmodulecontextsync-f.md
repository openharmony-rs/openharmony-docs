# createModuleContextSync

## 导入模块

```TypeScript
import { application } from '@kit.AbilityKit';
```

<a id="createmodulecontextsync"></a>
## createModuleContextSync

```TypeScript
export function createModuleContextSync(context: Context, moduleName: string): Context
```

创建指定模块的上下文。创建出的模块上下文中[resourceManager.Configuration](../../apis-localization-kit/arkts-apis/arkts-localization-resourcemanager-configuration-c.md)资源继承自入参上下文，便于开发者获取[跨HAP/HSP包应用资源](docroot://quick-start/resource-categories-and-access.md#跨haphsp包应用资源)。

> **说明：**  
>  
> 由于创建模块上下文的过程涉及资源查询与初始化，耗时相对较长，在对应用流畅性要求较高的场景下，不建议频繁或多次调用createModuleContext接口创建多个Context实例，以免影响用户体验。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务API中使用。

<!--Device-application-export function createModuleContextSync(context: Context, moduleName: string): Context--><!--Device-application-export function createModuleContextSync(context: Context, moduleName: string): Context-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [Context](../../apis-arkui/arkts-components/arkts-arkui-context-t.md) | 是 | 表示应用上下文。 |
| moduleName | string | 是 | 表示应用模块名。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Context](../../apis-arkui/arkts-components/arkts-arkui-context-t.md) | 返回创建的上下文。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16000011](../errorcode-ability.md#16000011-上下文对象不存在) | 上下文不存在。 |
| 16000021 | 模块不存在。 |

