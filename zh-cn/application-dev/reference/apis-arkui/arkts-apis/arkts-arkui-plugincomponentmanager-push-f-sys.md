# push（系统接口）

## 导入模块

```TypeScript
import { PluginComponentTemplate } from '@kit.ArkUI';
```

<a id="push"></a>
## push

```TypeScript
function push(param: PushParameterForStage, callback: AsyncCallback<void>): void
```

插件组件push方法，用于发送其提供的模板信息。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-pluginComponentManager-function push(param: PushParameterForStage, callback: AsyncCallback<void>): void--><!--Device-pluginComponentManager-function push(param: PushParameterForStage, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| param | [PushParameterForStage](arkts-arkui-plugincomponentmanager-pushparameterforstage-i-sys.md) | 是 | stage模型的插件组件push参数。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 插件组件push事件回调。 |

