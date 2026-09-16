# push（系统接口）

## 导入模块

```TypeScript
import { pluginComponentManager, PluginComponentTemplate } from '@kit.ArkUI';
```

## push

```TypeScript
function push(param: PushParameterForStage, callback: AsyncCallback<void>): void
```

组件提供方向组件使用方主动发送组件与数据。适用于需要主动推送插件组件模板的场景，例如跨应用内容分享、应用内嵌入的外部插件组件内容动态更新等。push 由组件提供方主动发起推送，request 由组件使用方主动发起请求；注意两者参数结构相近但 owner/target 含义相反，请勿混用。组件使用方需通过onPush事件监听接收数据，事件监听接口请参见@ohos.pluginComponent (PluginComponentManager)。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| param | [PushParameterForStage](arkts-arkui-plugincomponentmanager-pushparameterforstage-i-sys.md) | 是 | 组件提供方要发送的参数。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 此次接口调用的异步回调。 |

**示例**

```TypeScript
import { pluginComponentManager } from '@kit.ArkUI';

pluginComponentManager.push(
  {
    want: {
      bundleName: "com.example.provider",
      abilityName: "com.example.provider.MainAbility",
    },
    name: "plugintemplate",
    data: {
      "key_1": "plugin component test",
      "key_2": 34234,
    },
    extraData: {
      "extra_str": "this is push event",
    },
    jsonPath: "",
  },
  (err) => {
    if (err) {
      console.error(`push_callback: err.code = ${err.code}, err.message = ${err.message}`);
      return;
    }
    console.info("push_callback: push ok!");
  }
)
```
