# on_string

## on_string

```TypeScript
function on(eventType: string, callback: OnPushEventCallback | OnRequestEventCallback): void
```

提供方监听"request"类型的事件，给使用方返回通过request接口主动请求的数据；使用方监听"push"类型的事件，接收提供方通过push接口主动推送的数据。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-pluginComponentManager-function on(eventType: string, callback: OnPushEventCallback | OnRequestEventCallback): void--><!--Device-pluginComponentManager-function on(eventType: string, callback: OnPushEventCallback | OnRequestEventCallback): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| eventType | string | 是 | 监听的事件类型，可选值为："push"、"request"。"push"：指组件提供方向使用方主动推送数据。"request"：指组件使用方向提供方主动请求数据。 |
| callback | [OnPushEventCallback](../../apis-na/arkts-apis/arkts-na-plugincomponentmanager-onpusheventcallback-t.md) \| [OnRequestEventCallback](../../apis-na/arkts-apis/arkts-na-plugincomponentmanager-onrequesteventcallback-t.md) | 是 | 对应监听回调， push事件对应回调类型为OnPushEventCallback，request事件对应回调类型为OnRequestEventCallback。 |

## 示例

```TypeScript
import { pluginComponentManager, PluginComponentTemplate } from '@kit.ArkUI';
import { Want } from '@kit.AbilityKit';

const onPushListener = (source:Want, template:PluginComponentTemplate, data:pluginComponentManager.KVObject, extraData:pluginComponentManager.KVObject) => {
  console.info("onPushListener template.source=" + template.source);
  console.info("onPushListener source=" + JSON.stringify(source));
  console.info("onPushListener template=" + JSON.stringify(template));
  console.info("onPushListener data=" + JSON.stringify(data));
  console.info("onPushListener extraData=" + JSON.stringify(extraData));
}
const onRequestListener = (source:Want, name:string, data:pluginComponentManager.KVObject) => {
  console.info("onRequestListener");
  console.info("onRequestListener source=" + JSON.stringify(source));
  console.info("onRequestListener name=" + name);
  console.info("onRequestListener data=" + JSON.stringify(data));
  let returnData: Record<string, string | pluginComponentManager.KVObject> = { "template": "ets/pages/plugin.js", "data": data };
  return returnData;
}
pluginComponentManager.on("push", onPushListener);
pluginComponentManager.on("request", onRequestListener);
```

