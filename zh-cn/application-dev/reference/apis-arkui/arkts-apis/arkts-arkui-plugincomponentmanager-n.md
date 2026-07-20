# pluginComponentManager

插件组件管理器接口。

**起始版本：** 12

<!--Device-unnamed-declare namespace pluginComponentManager--><!--Device-unnamed-declare namespace pluginComponentManager-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { PluginComponentTemplate } from '@kit.ArkUI';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [push](arkts-arkui-plugincomponentmanager-push-f.md#push) | 插件组件push方法。 |
| [request](arkts-arkui-plugincomponentmanager-request-f.md#request) | 插件组件request方法。 |
| [on](arkts-arkui-plugincomponentmanager-on-f.md#on) | 插件组件事件监听。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [push](arkts-arkui-plugincomponentmanager-push-f-sys.md#push-1) | 插件组件push方法，用于发送其提供的模板信息。 |
| [request](arkts-arkui-plugincomponentmanager-request-f-sys.md#request-1) | 插件组件request方法，用于发送其所需模板信息的请求。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [PushParameters](arkts-arkui-plugincomponentmanager-pushparameters-i.md) | 插件组件push参数。 |
| [RequestParameters](arkts-arkui-plugincomponentmanager-requestparameters-i.md) | 插件组件request参数。 |
| [RequestCallbackParameters](arkts-arkui-plugincomponentmanager-requestcallbackparameters-i.md) | 插件组件request回调参数。 |
| [RequestEventResult](arkts-arkui-plugincomponentmanager-requesteventresult-i.md) | 插件组件request事件结果值。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [PushParameterForStage](arkts-arkui-plugincomponentmanager-pushparameterforstage-i-sys.md) | 在push函数中使用的插件组件push参数。 |
| [RequestParameterForStage](arkts-arkui-plugincomponentmanager-requestparameterforstage-i-sys.md) | 在request函数中使用的插件组件request参数。 |
<!--DelEnd-->

### 类型

| 名称 | 说明 |
| --- | --- |
| [KVObject](arkts-arkui-plugincomponentmanager-kvobject-t.md) | 定义KVObject |
| [OnPushEventCallback](arkts-arkui-plugincomponentmanager-onpusheventcallback-t.md) | 插件组件push事件回调。 |
| [OnRequestEventCallback](arkts-arkui-plugincomponentmanager-onrequesteventcallback-t.md) | 插件组件request事件回调。 |

