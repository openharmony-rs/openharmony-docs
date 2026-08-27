# OnRequestEventCallback

```TypeScript
type OnRequestEventCallback = (source: Want, name: string, data: KVObject) => RequestEventResult
```

对应request事件的监听回调函数。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| source | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 | request请求发送方相关信息。 |
| name | string | 是 | 请求的组件名称。 |
| data | [KVObject](arkts-arkui-plugincomponentmanager-kvobject-t.md) | 是 | request事件中传递的数据内容，以键值对形式存储，键和值类型由业务定义。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [RequestEventResult](arkts-arkui-plugincomponentmanager-requesteventresult-i.md) | 返回request事件结果。 |

**示例**

```TypeScript
import { pluginComponentManager } from '@kit.ArkUI';
import { Want } from '@kit.AbilityKit';

const onRequestListener = (source: Want, name: string, data: pluginComponentManager.KVObject) => {
  console.info("onRequestListener");
  console.info("onRequestListener source=" + JSON.stringify(source));
  console.info("onRequestListener name=" + name);
  console.info("onRequestListener data=" + JSON.stringify(data));
  // 构建Request事件回调的返回数据，指定组件模板路径并携带请求数据返回给请求方
  let returnData: Record<string, string | pluginComponentManager.KVObject> = {
    "template": "ets/pages/plugin.js",
    "data": data,
  }
  return returnData;
}
```
