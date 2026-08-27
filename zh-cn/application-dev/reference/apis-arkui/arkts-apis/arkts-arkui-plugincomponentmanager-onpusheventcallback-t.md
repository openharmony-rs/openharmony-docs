# OnPushEventCallback

```TypeScript
type OnPushEventCallback = (source: Want, template: PluginComponentTemplate, data: KVObject,
    extraData: KVObject) => void
```

对应push事件的监听回调函数。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| source | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 | push事件发送方相关信息。 |
| template | [PluginComponentTemplate](arkts-arkui-plugincomponent-plugincomponenttemplate-i.md) | 是 | 组件模板。 |
| data | [KVObject](arkts-arkui-plugincomponentmanager-kvobject-t.md) | 是 | push事件中传递的数据内容，以键值对形式存储，键和值类型由业务定义。 |
| extraData | [KVObject](arkts-arkui-plugincomponentmanager-kvobject-t.md) | 是 | push事件中传递的附加数据，以键值对形式存储，键和值类型由业务定义。 |

**示例**

```TypeScript
import { pluginComponentManager, PluginComponentTemplate } from '@kit.ArkUI';
import { Want } from '@kit.AbilityKit';

const onPushListener = (source: Want, template: PluginComponentTemplate, data: pluginComponentManager.KVObject, extraData: pluginComponentManager.KVObject) => {
  console.info("onPushListener template.source=" + template.source);
  console.info("onPushListener source=" + JSON.stringify(source));
  console.info("onPushListener template=" + JSON.stringify(template));
  console.info("onPushListener data=" + JSON.stringify(data));
  console.info("onPushListener extraData=" + JSON.stringify(extraData));
};
```
