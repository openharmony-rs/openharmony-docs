# @ohos.router

Router提供页面跳转能力，包括跳转到应用内的指定页面、同应用内的某个页面替换当前页面、返回上一页面或指定的页面等。 推荐使用[Navigation组件](../../../ui/arkts-navigation-architecture.md)作为应用路由框架。 > **说明：** > > - 页面路由需要在页面渲染完成之后才能调用，在onInit和onReady生命周期中页面还处于渲染阶段，禁止调用页面路由方法。 > > - 本模块功能依赖UI的执行上下文，不可在[UI上下文不明确](../../../ui/arkts-global-interface.md#ui上下文不明确)的地方使用，参见 > [UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md#UIContext)说明。 > > - 如果使用传入callback形式的 > [pushUrl](arkts-arkui-arkui-uicontext-router-c.md#pushUrl) > 或 > [pushNamedRoute](arkts-arkui-arkui-uicontext-router-c.md#pushNamedRoute) > 接口，callback中通过[getLength](arkts-arkui-arkui-uicontext-router-c.md#getLength)等接口获取的栈信息为中间态的栈信息，可能与栈操作完全结束后，再通过 > [getLength](arkts-arkui-arkui-uicontext-router-c.md#getLength)等接口获取的栈信息不一致。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** -1

<!--Device-unnamed-declare namespace router--><!--Device-unnamed-declare namespace router-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [back](arkts-arkui-router-back-f.md#back) | 返回上一页面或指定的页面，会删除当前页面与指定页面之间的所有页面。如果此前调用了showAlertBeforeBackPage 开启了返回询问对话框，则在执行返回操作时会先弹出确认对话框，用户确认后才执行返回；用户取消则不执行返回。 |
| [back](arkts-arkui-router-back-f.md#back) | 返回指定的页面，会删除当前页面与指定页面之间的所有页面。如果此前调用了showAlertBeforeBackPage 开启了返回询问对话框，则在执行返回操作时会先弹出确认对话框，用户确认后才执行返回；用户取消则不执行返回。 |
| [clear](arkts-arkui-router-clear-f.md#clear) | 清空页面栈中的所有历史页面，仅保留当前页面作为栈顶页面。 |
| [disableAlertBeforeBackPage](arkts-arkui-router-disablealertbeforebackpage-f.md#disableAlertBeforeBackPage) | 禁用页面返回询问对话框。适用于用户已完成保存操作可以安全返回、页面状态切换后不再需要返回确认、需要动态控制返回行为等场景。与showAlertBeforeBackPage()方法成对使用：调用showAlertBeforeBackPage()开启对话框后，可在适当时机调用本方法关闭对话框。 |
| [enableAlertBeforeBackPage](arkts-arkui-router-enablealertbeforebackpage-f.md#enableAlertBeforeBackPage) | 开启页面返回询问对话框。调用此方法后，执行back返回页面时将弹出确认对话框，用户确认后才执行页面返回操作。 适用于需要防止用户误操作返回导致数据丢失的场景，例如用户正在填写表单、编辑文档或进行支付操作时，弹出确认对话框以避免意外退出。 |
| [getLength](arkts-arkui-router-getlength-f.md#getLength) | 获取当前在页面栈内的页面数量。 |
| [getParams](arkts-arkui-router-getparams-f.md#getParams) | 获取发起跳转的页面往当前页传入的参数。 |
| [getState](arkts-arkui-router-getstate-f.md#getState) | 获取栈顶页面的状态信息。 |
| [getStateByIndex](arkts-arkui-router-getstatebyindex-f.md#getStateByIndex) | 通过索引值获取对应页面的状态信息。 |
| [getStateByUrl](arkts-arkui-router-getstatebyurl-f.md#getStateByUrl) | 通过url获取对应页面的状态信息。 |
| [hideAlertBeforeBackPage](arkts-arkui-router-hidealertbeforebackpage-f.md#hideAlertBeforeBackPage) | 禁用页面返回询问对话框。调用此方法后，将关闭由showAlertBeforeBackPage 开启的返回询问对话框，back操作将不再弹出确认对话框，直接执行页面返回。 |
| [push](arkts-arkui-router-push-f.md#push) | 跳转到应用内的指定页面。 |
| [pushNamedRoute](arkts-arkui-router-pushnamedroute-f.md#pushNamedRoute) | 跳转到指定的命名路由页面。 |
| [pushNamedRoute](arkts-arkui-router-pushnamedroute-f.md#pushNamedRoute) | 跳转到指定的命名路由页面。 |
| [pushNamedRoute](arkts-arkui-router-pushnamedroute-f.md#pushNamedRoute) | 跳转到指定的命名路由页面。 |
| [pushNamedRoute](arkts-arkui-router-pushnamedroute-f.md#pushNamedRoute) | 跳转到指定的命名路由页面。 |
| [pushUrl](arkts-arkui-router-pushurl-f.md#pushUrl) | 跳转到应用内的指定页面。 |
| [pushUrl](arkts-arkui-router-pushurl-f.md#pushUrl) | 跳转到应用内的指定页面。 |
| [pushUrl](arkts-arkui-router-pushurl-f.md#pushUrl) | 跳转到应用内的指定页面。 |
| [pushUrl](arkts-arkui-router-pushurl-f.md#pushUrl) | 跳转到应用内的指定页面。 |
| [replace](arkts-arkui-router-replace-f.md#replace) | 用应用内的某个页面替换当前页面，并销毁被替换的页面。不支持设置页面转场动效，如需设置，推荐使用[Navigation组件](../../../ui/arkts-navigation-architecture.md)。 |
| [replaceNamedRoute](arkts-arkui-router-replacenamedroute-f.md#replaceNamedRoute) | 用指定的命名路由页面替换当前页面，并销毁被替换的页面。不支持设置页面转场动效，如需设置，推荐使用[Navigation组件](../../../ui/arkts-navigation-architecture.md)。 |
| [replaceNamedRoute](arkts-arkui-router-replacenamedroute-f.md#replaceNamedRoute) | 用指定的命名路由页面替换当前页面，并销毁被替换的页面。不支持设置页面转场动效，如需设置，推荐使用[Navigation组件](../../../ui/arkts-navigation-architecture.md)。 |
| [replaceNamedRoute](arkts-arkui-router-replacenamedroute-f.md#replaceNamedRoute) | 用指定的命名路由页面替换当前页面，并销毁被替换的页面。不支持设置页面转场动效，如需设置，推荐使用[Navigation组件](../../../ui/arkts-navigation-architecture.md)。 |
| [replaceNamedRoute](arkts-arkui-router-replacenamedroute-f.md#replaceNamedRoute) | 用指定的命名路由页面替换当前页面，并销毁被替换的页面。不支持设置页面转场动效，如需设置，推荐使用[Navigation组件](../../../ui/arkts-navigation-architecture.md)。 |
| [replaceUrl](arkts-arkui-router-replaceurl-f.md#replaceUrl) | 用应用内的某个页面替换当前页面，并销毁被替换的页面。不支持设置页面转场动效，如需设置，推荐使用[Navigation组件](../../../ui/arkts-navigation-architecture.md)。 |
| [replaceUrl](arkts-arkui-router-replaceurl-f.md#replaceUrl) | 用应用内的某个页面替换当前页面，并销毁被替换的页面。不支持设置页面转场动效，如需设置，推荐使用[Navigation组件](../../../ui/arkts-navigation-architecture.md)。 |
| [replaceUrl](arkts-arkui-router-replaceurl-f.md#replaceUrl) | 用应用内的某个页面替换当前页面，并销毁被替换的页面。不支持设置页面转场动效，如需设置，推荐使用[Navigation组件](../../../ui/arkts-navigation-architecture.md)。 |
| [replaceUrl](arkts-arkui-router-replaceurl-f.md#replaceUrl) | 用应用内的某个页面替换当前页面，并销毁被替换的页面。不支持设置页面转场动效，如需设置，推荐使用[Navigation组件](../../../ui/arkts-navigation-architecture.md)。 |
| [showAlertBeforeBackPage](arkts-arkui-router-showalertbeforebackpage-f.md#showAlertBeforeBackPage) | 开启页面返回询问对话框。调用此方法后，执行back返回页面时将弹出确认对话框，用户确认后才执行页面返回操作。 适用于需要防止用户误操作返回导致数据丢失的场景，例如用户正在填写表单、编辑文档或进行支付操作时，弹出确认对话框以避免意外退出。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [EnableAlertOptions](arkts-arkui-router-enablealertoptions-i.md) | 页面状态信息。 |
| [NamedRouterOptions](arkts-arkui-router-namedrouteroptions-i.md) | 命名路由跳转选项。 |
| [RouterOptions](arkts-arkui-router-routeroptions-i.md) | 路由跳转选项。 |
| [RouterState](arkts-arkui-router-routerstate-i.md) | 页面状态信息。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [RouterMode](arkts-arkui-router-routermode-e.md) | 路由跳转模式。 |

