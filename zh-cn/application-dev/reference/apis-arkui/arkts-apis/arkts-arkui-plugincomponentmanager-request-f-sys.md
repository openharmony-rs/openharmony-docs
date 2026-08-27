# request（系统接口）

## 导入模块

```TypeScript
import { pluginComponentManager, PluginComponentTemplate } from '@kit.ArkUI';
```

## request

```TypeScript
function request(param: RequestParameterForStage, callback: AsyncCallback<RequestCallbackParameters>): void
```

组件使用方向组件提供方主动请求组件。组件提供方需通过onRequest事件监听响应请求，并通过回调返回组件模板信息。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| param | [RequestParameterForStage](arkts-arkui-plugincomponentmanager-requestparameterforstage-i-sys.md) | 是 | 组件模板的详细请求信息。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[RequestCallbackParameters](arkts-arkui-plugincomponentmanager-requestcallbackparameters-i.md)&gt; | 是 | 此次请求的异步回调，通过回调接口的参数返回请求响应的数据。 |

**示例**

```TypeScript
import { pluginComponentManager } from '@kit.ArkUI';

pluginComponentManager.request(
  {
    owner: {
      bundleName: "com.example.user",
      abilityName: "com.example.user.MainAbility",
    },
    target: {
      bundleName: "com.example.provider",
      abilityName: "com.example.provider.MainAbility",
    },
    name: "plugintemplate",
    data: {
      "key1": "myapplication plugin component test",
    },
    jsonPath: "",
  },
  (err, data) => {
    if (err) {
      console.error(`Failed to request. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    if (!data) {
      return;
    }
    console.info("request_callback: componentTemplate.ability=" + data.componentTemplate.ability);
    console.info("request_callback: componentTemplate.source=" + data.componentTemplate.source);
  }
);
```
