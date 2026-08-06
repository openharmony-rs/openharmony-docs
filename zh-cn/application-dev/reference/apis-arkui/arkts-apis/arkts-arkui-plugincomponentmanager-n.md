# pluginComponentManager

插件组件管理器，提供插件组件的请求、推送和事件监听等管理能力。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-declare namespace pluginComponentManager--><!--Device-unnamed-declare namespace pluginComponentManager-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [push](arkts-arkui-plugincomponentmanager-push-f.md#push) | 组件提供方向组件使用方主动发送组件和数据。适用于提供方数据更新后需主动通知使用方刷新显示的场景。 |
| [request](arkts-arkui-plugincomponentmanager-request-f.md#request) | 组件使用方向组件提供方主动请求组件。适用于使用方需按需获取提供方组件及数据的场景。 |
| [on](arkts-arkui-plugincomponentmanager-on-f.md#on) | 提供方监听"request"类型的事件，给使用方返回通过request接口主动请求的数据；使用方监听"push"类型的事件，接收提供方通过push接口主动推送的数据。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [push](arkts-arkui-plugincomponentmanager-push-f-sys.md#push-1) | 组件提供方向组件使用方主动发送组件与数据。组件使用方需通过onPush事件监听接收数据。 |
| [request](arkts-arkui-plugincomponentmanager-request-f-sys.md#request-1) | 组件使用方向组件提供方主动请求组件。组件提供方需通过onRequest事件监听响应请求，并通过回调返回组件模板信息。 |
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

