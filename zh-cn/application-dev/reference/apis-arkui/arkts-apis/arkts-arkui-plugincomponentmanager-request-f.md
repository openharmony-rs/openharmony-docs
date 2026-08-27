# request

## 导入模块

```TypeScript
import { pluginComponentManager, PluginComponentTemplate } from '@kit.ArkUI';
```

## request

```TypeScript
function request(param: RequestParameters, callback: AsyncCallback<RequestCallbackParameters>): void
```

组件使用方向组件提供方主动请求组件。适用于使用方需按需获取提供方组件及数据的场景。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| param | [RequestParameters](arkts-arkui-plugincomponentmanager-requestparameters-i.md) | 是 | 组件模板的详细请求信息。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[RequestCallbackParameters](arkts-arkui-plugincomponentmanager-requestcallbackparameters-i.md)&gt; | 是 | 此次请求的异步回调，通过回调接口的参数返回请求所获取的数据。 |

**示例**

```TypeScript
import { pluginComponentManager } from '@kit.ArkUI';

pluginComponentManager.request(
  {
    want: {
      bundleName: "com.example.provider",
      abilityName: "com.example.provider.MainAbility",
    },
    name: "plugintemplate",
    data: {
      "key_1": "plugin component test",
      "key_2": 1111111,
    },
    jsonPath: "",
  },
  (err, data) => {
    if (err) {
      console.error(`request_callback: err.code = ${err.code}, err.message = ${err.message}`);
      return;
    }
    console.info("request_callback: componentTemplate.ability=" + data.componentTemplate.ability);
    console.info("request_callback: componentTemplate.source=" + data.componentTemplate.source);
    console.info("request_callback: data=" + JSON.stringify(data.data));
    console.info("request_callback: extraData=" + JSON.stringify(data.extraData));
  }
)
```
