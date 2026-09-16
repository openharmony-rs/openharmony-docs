# pluginComponentManager(PluginComponentManager)

插件组件管理器，提供插件组件的请求、推送和事件监听等管理能力。

**起始版本：** 8

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { pluginComponentManager, PluginComponentTemplate } from '@kit.ArkUI';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [push](arkts-arkui-plugincomponentmanager-push-f.md) | 组件提供方向组件使用方主动发送组件与数据。适用于需要主动推送插件组件模板的场景，例如跨应用内容分享、应用内嵌入的外部插件组件内容动态更新等。push 由组件提供方主动发起推送，request 由组件使用方主动发起请求；注意两者参数结构相近但 owner/target 含义相反，请勿混用。组件使用方需通过onPush事件监听接收数据，事件监听接口请参见@ohos.pluginComponent (PluginComponentManager)。 |
| [request](arkts-arkui-plugincomponentmanager-request-f.md) | 组件使用方向组件提供方主动请求组件。适用于使用方需要按需动态获取插件组件模板的场景，例如动态加载其他应用提供的插件内容、按需展示跨应用组件等。组件提供方需通过onRequest事件监听响应请求，并通过回调返回组件模板信息，事件监听接口请参见@ohos.pluginComponent (PluginComponentManager)。 |
| [on](arkts-arkui-plugincomponentmanager-on-f.md) | 提供方监听"request"类型的事件，给使用方返回通过request接口主动请求的数据；使用方监听"push"类型的事件，接收提供方通过push接口主动推送的数据。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [push](arkts-arkui-plugincomponentmanager-push-f-sys.md) | 组件提供方向组件使用方主动发送组件与数据。适用于需要主动推送插件组件模板的场景，例如跨应用内容分享、应用内嵌入的外部插件组件内容动态更新等。push 由组件提供方主动发起推送，request 由组件使用方主动发起请求；注意两者参数结构相近但 owner/target 含义相反，请勿混用。组件使用方需通过onPush事件监听接收数据，事件监听接口请参见@ohos.pluginComponent (PluginComponentManager)。 |
| [request](arkts-arkui-plugincomponentmanager-request-f-sys.md) | 组件使用方向组件提供方主动请求组件。适用于使用方需要按需动态获取插件组件模板的场景，例如动态加载其他应用提供的插件内容、按需展示跨应用组件等。组件提供方需通过onRequest事件监听响应请求，并通过回调返回组件模板信息，事件监听接口请参见@ohos.pluginComponent (PluginComponentManager)。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [PushParameters](arkts-arkui-plugincomponentmanager-pushparameters-i.md) | 使用pluginComponentManager.push方法时需要传递的参数。 |
| [RequestParameters](arkts-arkui-plugincomponentmanager-requestparameters-i.md) | 使用pluginComponentManager.request方法时需要传递的参数。 |
| [RequestCallbackParameters](arkts-arkui-plugincomponentmanager-requestcallbackparameters-i.md) | pluginComponentManager.request方法接收到的回调结果。 |
| [RequestEventResult](arkts-arkui-plugincomponentmanager-requesteventresult-i.md) | 注册request监听方法后，接收到请求事件时回应请求的数据类型。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [PushParameterForStage](arkts-arkui-plugincomponentmanager-pushparameterforstage-i-sys.md) | 用于设置Stage模型下使用pluginComponentManager.push方法时需要传递的参数。 |
| [RequestParameterForStage](arkts-arkui-plugincomponentmanager-requestparameterforstage-i-sys.md) | 用于设置Stage模型下使用pluginComponentManager.request方法时需要传递的参数。 |
<!--DelEnd-->

### 类型

| 名称 | 说明 |
| --- | --- |
| [KVObject](arkts-arkui-plugincomponentmanager-kvobject-t.md) | 以键值对形式存储信息，符合JSON格式。 |
| [OnPushEventCallback](arkts-arkui-plugincomponentmanager-onpusheventcallback-t.md) | 对应push事件的监听回调函数。 |
| [OnRequestEventCallback](arkts-arkui-plugincomponentmanager-onrequesteventcallback-t.md) | 对应request事件的监听回调函数。 |
