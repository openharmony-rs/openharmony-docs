# @ohos.selectionInput.SelectionExtensionAbility

## 导入模块

```TypeScript
import { SelectionExtensionAbility } from '@kit.BasicServicesKit';
```

## 汇总

<!--Del-->
### 类（系统接口）

| 名称 | 说明 |
| --- | --- |
| [SelectionExtensionAbility](arkts-basicservices-selectioninput-selectionextensionability-selectionextensionability-c-sys.md) | 本模块提供划词扩展能力，支持开发者通过继承SelectionExtensionAbility实现自定义的划词扩展服务，适用于在用户通过鼠标、触控板选中文本后提供搜索、翻译等扩展交互的场景。开发者需在工程配置中声明该 ExtensionAbility。具体的配置请参见 [实现一个划词扩展能力](../../../basic-services/selectionInput/selection-services-application-guide.md)。本模块提供的具体能力包括： - 生命周期管理：通过[onConnect](arkts-basicservices-selectioninput-selectionextensionability-selectionextensionability-c-sys.md#onconnect)和 [onDisconnect](arkts-basicservices-selectioninput-selectionextensionability-selectionextensionability-c-sys.md#ondisconnect)回调处理连接与断开逻辑。 - 提供context属性：开发者可通过context调用 [startAbility](arkts-basicservices-selectioninput-selectionextensioncontext-selectionextensioncontext-c-sys.md#startability)拉起同应用内的目标 Ability，或将context作为[createPanel](arkts-basicservices-selectionmanager-createpanel-f-sys.md)的入参创建划词面板。 |
<!--DelEnd-->

