# WindowStage

窗口管理器。管理各个基本窗口单元，即[Window](arkts-window.md)实例。

下列API示例中都需在[onWindowStageCreate()](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-uiability-uiability-c.md#onwindowstagecreate)函数中使用WindowStage的实例调用对应方法。

**起始版本：** 9

<!--Device-window-interface WindowStage--><!--Device-window-interface WindowStage-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

## 导入模块

```TypeScript
import { window } from '@kit.ArkUI';
```

## createSubWindow

```TypeScript
createSubWindow(name: string): Promise<Window>
```

创建该WindowStage实例下的子窗口，使用Promise异步回调。

子窗口创建后默认是[沉浸式布局](../../windowmanager/window-terminology.md#沉浸式布局)。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WindowStage-createSubWindow(name: string): Promise<Window>--><!--Device-WindowStage-createSubWindow(name: string): Promise<Window>-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 子窗口的名字。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Window&gt; | Promise对象。返回当前WindowStage下的子窗口对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible cause: Incorrect parameter types. |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal.Possible cause: The subWindow has been created and can not be created again. |
| [1300005](../errorcode-window.md#1300005-windowstage异常) | This window stage is abnormal.<br>**适用版本：** 9+ |

## createSubWindow

```TypeScript
createSubWindow(name: string, callback: AsyncCallback<Window>): void
```

创建该WindowStage实例下的子窗口，使用callback异步回调。

子窗口创建后默认是[沉浸式布局](../../windowmanager/window-terminology.md#沉浸式布局)。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WindowStage-createSubWindow(name: string, callback: AsyncCallback<Window>): void--><!--Device-WindowStage-createSubWindow(name: string, callback: AsyncCallback<Window>): void-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 子窗口的名字。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Window&gt; | 是 | 回调函数。返回当前WindowStage下的子窗口对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible cause: Incorrect parameter types. |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal.Possible cause: The subWindow has been created and can not be created again. |
| [1300005](../errorcode-window.md#1300005-windowstage异常) | This window stage is abnormal.<br>**适用版本：** 9+ |

## createSubWindowWithOptions

```TypeScript
createSubWindowWithOptions(name: string, options: SubWindowOptions): Promise<Window>
```

创建该WindowStage实例下的子窗口，使用Promise异步回调。

非[自由窗口](../../windowmanager/window-terminology.md#自由窗口)状态下，子窗口创建后默认是[沉浸式布局](../../windowmanager/window-terminology.md#沉浸式布局)。

自由窗口状态下，子窗口参数[decorEnabled](arkts-apis-window-i.md#subwindowoptions11)为false时，子窗口创建后为沉浸式布局；子窗口参数decorEnabled为true，子窗口创建后为非沉浸式布局。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WindowStage-createSubWindowWithOptions(name: string, options: SubWindowOptions): Promise<Window>--><!--Device-WindowStage-createSubWindowWithOptions(name: string, options: SubWindowOptions): Promise<Window>-End-->

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 子窗口的名字。 |
| options | [SubWindowOptions](arkts-arkui-window-subwindowoptions-i.md) | 是 | 子窗口参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Window&gt; | Promise used to return the subwindow. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible cause: Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal.Possible cause: 1. The window is not created or destroyed;2. The subWindow has been created and can not be created again. |
| [1300005](../errorcode-window.md#1300005-windowstage异常) | This window stage is abnormal. |

## getMainWindow

```TypeScript
getMainWindow(): Promise<Window>
```

获取该WindowStage实例下的主窗口，使用Promise异步回调。

调用该接口前，建议先通过[loadContent](../apis-arkui/arkts-apis-window-WindowStage.md#loadcontent9)方法或者[setUIContent](arkts-apis-window-Window.md#setuicontent9-1)方法完成页面加载。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WindowStage-getMainWindow(): Promise<Window>--><!--Device-WindowStage-getMainWindow(): Promise<Window>-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Window&gt; | Promise对象。返回当前WindowStage下的主窗口对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal.Possible cause: The window is not created or destroyed. |
| [1300005](../errorcode-window.md#1300005-windowstage异常) | This window stage is abnormal. |

## getMainWindow

```TypeScript
getMainWindow(callback: AsyncCallback<Window>): void
```

获取该WindowStage实例下的主窗口，使用callback异步回调。

调用该接口前，建议先通过[loadContent](../apis-arkui/arkts-apis-window-WindowStage.md#loadcontent9)方法或者[setUIContent](arkts-apis-window-Window.md#setuicontent9-1)方法完成页面加载。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WindowStage-getMainWindow(callback: AsyncCallback<Window>): void--><!--Device-WindowStage-getMainWindow(callback: AsyncCallback<Window>): void-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Window&gt; | 是 | 回调函数。返回当前WindowStage下的主窗口对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal.Possible cause: The window is not created or destroyed. |
| [1300005](../errorcode-window.md#1300005-windowstage异常) | This window stage is abnormal. |

## getMainWindowSync

```TypeScript
getMainWindowSync(): Window
```

获取该WindowStage实例下的主窗口，该接口为同步调用。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WindowStage-getMainWindowSync(): Window--><!--Device-WindowStage-getMainWindowSync(): Window-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Window](arkts-arkui-window-window-i.md) | 返回当前WindowStage下的主窗口对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1300005](../errorcode-window.md#1300005-windowstage异常) | This window stage is abnormal. |

## getSubWindow

```TypeScript
getSubWindow(): Promise<Array<Window>>
```

获取该WindowStage实例下的所有子窗口，使用Promise异步回调。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WindowStage-getSubWindow(): Promise<Array<Window>>--><!--Device-WindowStage-getSubWindow(): Promise<Array<Window>>-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;Window&gt;&gt; | Promise对象。返回当前WindowStage下的所有子窗口对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1300005](../errorcode-window.md#1300005-windowstage异常) | This window stage is abnormal.<br>**适用版本：** 9+ |

## getSubWindow

```TypeScript
getSubWindow(callback: AsyncCallback<Array<Window>>): void
```

获取该WindowStage实例下的所有子窗口，使用callback异步回调。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WindowStage-getSubWindow(callback: AsyncCallback<Array<Window>>): void--><!--Device-WindowStage-getSubWindow(callback: AsyncCallback<Array<Window>>): void-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;Window&gt;&gt; | 是 | 回调函数。返回当前WindowStage下的所有子窗口对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal.<br>**适用版本：** 10+ |
| [1300005](../errorcode-window.md#1300005-windowstage异常) | This window stage is abnormal.<br>**适用版本：** 9+ |

## isWindowRectAutoSave

```TypeScript
isWindowRectAutoSave(): Promise<boolean>
```

判断当前主窗口是否已经启用尺寸记忆，使用Promise异步回调。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-WindowStage-isWindowRectAutoSave(): Promise<boolean>--><!--Device-WindowStage-isWindowRectAutoSave(): Promise<boolean>-End-->

**系统能力：** SystemCapability.Window.SessionManager

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象。返回true表示当前窗口启用尺寸记忆，返回false表示当前窗口禁用尺寸记忆。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal.Possible cause: 1. The window is not created or destroyed;2. Internal task error. |
| [1300003](../errorcode-window.md#1300003-系统服务工作异常) | This window manager service works abnormally.<br>**适用版本：** 20+ |

## loadContent

```TypeScript
loadContent(path: string, storage: LocalStorage, callback: AsyncCallback<void>): void
```

根据当前工程中指定的页面路径为窗口加载具体页面内容，通过LocalStorage传递状态属性给加载的页面，使用callback异步回调。

建议在UIAbility启动过程中使用该接口，重复调用将先销毁旧的页面内容（即UIContent）再加载新的页面内容，请谨慎使用。

当前UI的执行上下文可能不明确，所以不建议在本接口的回调函数中做UI相关的操作。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WindowStage-loadContent(path: string, storage: LocalStorage, callback: AsyncCallback<void>): void--><!--Device-WindowStage-loadContent(path: string, storage: LocalStorage, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 要加载到窗口中的页面内容的路径，该路径需添加到工程的main_pages.json文件中。不支持相对路径写法，需与main_pages.json中的src取值保持一致。 |
| storage | [LocalStorage](arkts-arkui-localstorage-c.md) | 是 | 页面级UI状态存储单元，这里用于为加载到窗口的页面内容传递状态属性。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible cause:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Invalid path parameter. |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal.Possible cause: The window is not created or destroyed. |
| [1300005](../errorcode-window.md#1300005-windowstage异常) | This window stage is abnormal.<br>**适用版本：** 9+ |

## loadContent

```TypeScript
loadContent(path: string, storage?: LocalStorage): Promise<void>
```

根据当前工程中指定的页面路径为WindowStage的主窗口加载具体页面内容，通过LocalStorage传递状态属性给加载的页面，使用Promise异步回调。

建议在UIAbility启动过程中调用该接口，重复调用将首先销毁旧的页面内容（即UIContent）再加载新页面内容，请谨慎使用。当前UI的执行上下文可能不明确，所以不建议在回调函数中做UI相关的操作。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WindowStage-loadContent(path: string, storage?: LocalStorage): Promise<void>--><!--Device-WindowStage-loadContent(path: string, storage?: LocalStorage): Promise<void>-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 要加载到窗口中的页面内容的路径，该路径需添加到工程的main_pages.json文件中。不支持相对路径写法，需与main_pages.json中的src取值保持一致。 |
| storage | [LocalStorage](arkts-arkui-localstorage-c.md) | 否 | 页面级UI状态存储单元，为加载到窗口的页面内容传递状态属性，默认值为空。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal.Possible cause: The window is not created or destroyed. |
| [1300005](../errorcode-window.md#1300005-windowstage异常) | This window stage is abnormal.<br>**适用版本：** 9+ |

## loadContent

```TypeScript
loadContent(path: string, callback: AsyncCallback<void>): void
```

为当前窗口加载具体页面内容，使用callback异步回调。

建议在UIAbility启动过程中使用该接口，多次调用该接口会先销毁旧的页面内容（即UIContent）再加载新的页面内容，请谨慎使用。

当前UI的执行上下文可能不明确，所以不建议在本接口的回调函数中做UI相关的操作。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WindowStage-loadContent(path: string, callback: AsyncCallback<void>): void--><!--Device-WindowStage-loadContent(path: string, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 要加载到窗口中的页面内容的路径，Stage模型下该路径需添加到工程的main_pages.json文件中，FA模型下该路径需添加到工程的config.json文件中。不支持相对路径写法，需与main_pages.json或config.json中的src取值保持一致。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible cause:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Invalid path parameter. |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal.Possible cause: The window is not created or destroyed. |
| [1300005](../errorcode-window.md#1300005-windowstage异常) | This window stage is abnormal.<br>**适用版本：** 9+ |

## loadContentByName

```TypeScript
loadContentByName(name: string, storage: LocalStorage, callback: AsyncCallback<void>): void
```

Loads content by named router

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WindowStage-loadContentByName(name: string, storage: LocalStorage, callback: AsyncCallback<void>): void--><!--Device-WindowStage-loadContentByName(name: string, storage: LocalStorage, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | name of the page to which the content will be loaded. |
| storage | [LocalStorage](arkts-arkui-localstorage-c.md) | 是 | The data object shared within the content instance loaded by the window. |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | Callback used to return the result. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types. |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal.Possible cause: The window is not created or destroyed. |

## loadContentByName

```TypeScript
loadContentByName(name: string, callback: AsyncCallback<void>): void
```

根据指定路由页面名称为当前窗口加载[命名路由](../../ui/arkts-routing.md#命名路由)页面，使用callback异步回调。

建议在UIAbility启动过程中使用该接口，重复调用该接口将先销毁旧的页面内容（即UIContent）再加载新的页面内容，请谨慎使用。

当前UI的执行上下文可能不明确，所以不建议在本接口的回调函数中做UI相关的操作。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WindowStage-loadContentByName(name: string, callback: AsyncCallback<void>): void--><!--Device-WindowStage-loadContentByName(name: string, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | name of the page to which the content will be loaded. |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | Callback used to return the result. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types. |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal.Possible cause: The window is not created or destroyed. |

## loadContentByName

```TypeScript
loadContentByName(name: string, storage?: LocalStorage): Promise<void>
```

Loads content by named router

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WindowStage-loadContentByName(name: string, storage?: LocalStorage): Promise<void>--><!--Device-WindowStage-loadContentByName(name: string, storage?: LocalStorage): Promise<void>-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | name of the page to which the content will be loaded. |
| storage | [LocalStorage](arkts-arkui-localstorage-c.md) | 否 | The data object shared within the content instance loaded by the window. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types. |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal.Possible cause: The window is not created or destroyed. |

## off

```TypeScript
off(eventType: 'windowStageEvent', callback?: Callback<WindowStageEventType>): void
```

关闭WindowStage生命周期变化的监听。

用于关闭[on('windowStageEvent')](#onwindowstageevent9)接口对WindowStage生命周期变化的监听。

如果没有调用[on('windowStageEvent')](#onwindowstageevent9)接口开启监听就关闭，程序正常执行不会抛出异常。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WindowStage-off(eventType: 'windowStageEvent', callback?: Callback<WindowStageEventType>): void--><!--Device-WindowStage-off(eventType: 'windowStageEvent', callback?: Callback<WindowStageEventType>): void-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| eventType | 'windowStageEvent' | 是 | 监听事件，固定为'windowStageEvent'，即WindowStage生命周期变化事件。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;WindowStageEventType&gt; | 否 | 回调函数。返回当前的WindowStage生命周期状态。若传入参数，则关闭该监听。若未传入参数，则关闭所有WindowStage生命周期变化的监听。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible cause: 1. Incorrect parameter types;2. Parameter verification failed. |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal. |
| [1300005](../errorcode-window.md#1300005-windowstage异常) | This window stage is abnormal. |

## off

```TypeScript
off(eventType: 'windowStageLifecycleEvent', callback?: Callback<WindowStageLifecycleEventType>): void
```

关闭WindowStage生命周期变化的监听。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WindowStage-off(eventType: 'windowStageLifecycleEvent', callback?: Callback<WindowStageLifecycleEventType>): void--><!--Device-WindowStage-off(eventType: 'windowStageLifecycleEvent', callback?: Callback<WindowStageLifecycleEventType>): void-End-->

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| eventType | 'windowStageLifecycleEvent' | 是 | 监听事件，固定为'windowStageLifecycleEvent'，即WindowStage生命周期变化事件。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;WindowStageLifecycleEventType&gt; | 否 | 回调函数。返回当前的WindowStage生命周期状态。若传入参数，则关闭该监听。若未传入参数，则关闭所有WindowStage生命周期变化的监听。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal. |
| [1300005](../errorcode-window.md#1300005-windowstage异常) | This window stage is abnormal. |

## off

```TypeScript
off(eventType: 'windowStageClose', callback?: Callback<void>): void
```

关闭主窗口关闭事件的监听。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-WindowStage-off(eventType: 'windowStageClose', callback?: Callback<void>): void--><!--Device-WindowStage-off(eventType: 'windowStageClose', callback?: Callback<void>): void-End-->

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| eventType | 'windowStageClose' | 是 | 监听事件，固定为'windowStageClose'，即关闭主窗口关闭事件的监听。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt; | 否 | 回调函数。当点击主窗口右上角关闭按钮事件发生时的回调。该回调函数不返回任何参数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal. |

## on

```TypeScript
on(eventType: 'windowStageEvent', callback: Callback<WindowStageEventType>): void
```

开启WindowStage生命周期变化的监听。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WindowStage-on(eventType: 'windowStageEvent', callback: Callback<WindowStageEventType>): void--><!--Device-WindowStage-on(eventType: 'windowStageEvent', callback: Callback<WindowStageEventType>): void-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| eventType | 'windowStageEvent' | 是 | 监听事件，固定为'windowStageEvent'，即WindowStage生命周期变化事件。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;WindowStageEventType&gt; | 是 | 回调函数。返回当前的WindowStage生命周期状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal. |
| [1300005](../errorcode-window.md#1300005-windowstage异常) | This window stage is abnormal. |

## on

```TypeScript
on(eventType: 'windowStageLifecycleEvent', callback: Callback<WindowStageLifecycleEventType>): void
```

开启WindowStage生命周期变化的监听。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WindowStage-on(eventType: 'windowStageLifecycleEvent', callback: Callback<WindowStageLifecycleEventType>): void--><!--Device-WindowStage-on(eventType: 'windowStageLifecycleEvent', callback: Callback<WindowStageLifecycleEventType>): void-End-->

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| eventType | 'windowStageLifecycleEvent' | 是 | 监听事件，固定为'windowStageLifecycleEvent'，即WindowStage生命周期变化事件。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;WindowStageLifecycleEventType&gt; | 是 | 回调函数。返回当前的WindowStage生命周期状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal. |
| [1300005](../errorcode-window.md#1300005-windowstage异常) | This window stage is abnormal. |

## on

```TypeScript
on(eventType: 'windowStageClose', callback: Callback<void>): void
```

开启点击主窗三键区的关闭按钮监听事件。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-WindowStage-on(eventType: 'windowStageClose', callback: Callback<void>): void--><!--Device-WindowStage-on(eventType: 'windowStageClose', callback: Callback<void>): void-End-->

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| eventType | 'windowStageClose' | 是 | The value is fixed at 'windowStageClose', indicating the window stage |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt; | 是 | Callback function requires a boolean return value to determine whether to |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal. |

## releaseUIContent

```TypeScript
releaseUIContent(): Promise<void>
```

释放

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WindowStage-releaseUIContent(): Promise<void>--><!--Device-WindowStage-releaseUIContent(): Promise<void>-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value, indicating successful completion.Throws exception if window state is abnormal. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal.Possible cause: The window is not created or destroyed. |

## removeStartingWindow

```TypeScript
removeStartingWindow(): Promise<void>
```

支持应用控制启动页消失时机。

此接口只对应用主窗口生效，且需要在module.json5配置文件abilities标签中的metadata标签下配置"enable.remove.starting.window"为"true"才会生效。

在标签配置为"true"的情况下，系统提供了启动页超时保护机制，若5s内未调用此接口，系统将自动移除启动页。

若标签配置为"false"或未配置标签，则此接口不生效，启动页将会在应用首帧渲染完成后自动移除。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-WindowStage-removeStartingWindow(): Promise<void>--><!--Device-WindowStage-removeStartingWindow(): Promise<void>-End-->

**系统能力：** SystemCapability.Window.SessionManager

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | - 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal.Possible cause: 1. The window stage is not created or destroyed;2. The main window is not created or destroyed;3. Internal task error. |
| [1300003](../errorcode-window.md#1300003-系统服务工作异常) | This window manager service works abnormally. |

## setCustomDensity

```TypeScript
setCustomDensity(density: number): void
```

支持应用主窗口自定义其显示大小缩放系数。

已创建的子窗和系统窗口不会立即跟随主窗的customDensity变化重新布局，而是在子窗或系统窗口下一次位置、大小、系统缩放大小等窗口布局信息变化时跟随主窗的customDensity变化重新布局。

当存在同时使用该接口和setDefaultDensityEnabled(true)的情况时，以最后调用的设置效果为准。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-WindowStage-setCustomDensity(density: number): void--><!--Device-WindowStage-setCustomDensity(density: number): void-End-->

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| density | number | 是 | 自定义显示大小缩放系数。该参数为浮点数，取值范围为[0.5, 4.0]或-1.0。4.0表示窗口可显示的最大显示大小缩放系数，-1.0表示窗口使用系统显示大小缩放系数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal. |
| [1300005](../errorcode-window.md#1300005-windowstage异常) | This window stage is abnormal. |

## setCustomDensity

```TypeScript
setCustomDensity(density: number, applyToSubWindow?: boolean): void
```

支持应用主窗口自定义其显示大小缩放系数。

已创建的子窗和系统窗口不会立即跟随主窗的customDensity变化重新布局，而是在子窗或系统窗口下一次位置、大小、系统缩放大小等窗口布局信息变化时跟随主窗的customDensity变化重新布局。

当存在同时使用该接口和setDefaultDensityEnabled(true)的情况时，以最后调用的设置效果为准。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WindowStage-setCustomDensity(density: double, applyToSubWindow?: boolean): void--><!--Device-WindowStage-setCustomDensity(density: double, applyToSubWindow?: boolean): void-End-->

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| density | number | 是 | 自定义显示大小缩放系数。该参数为浮点数，取值范围为[0.5, 4.0]或-1.0。4.0表示窗口可显示的最大显示大小缩放系数，-1.0表示窗口使用系统显示大小缩放系数。 |
| applyToSubWindow | boolean | 否 | 设置当前已创建的子窗和系统窗口是否立即跟随主窗口更新customDensity并重新布局。设置为true时，表示立即跟随主窗生效；设置为false时，表示不会立即跟随主窗生效，而是在子窗或系统窗口下一次位置、大小、系统缩放大小等窗口布局信息变化时跟随主窗的customDensity变化重新布局。默认值为false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal.Possible cause: The main window is not created or destroyed. |
| [1300005](../errorcode-window.md#1300005-windowstage异常) | This window stage is abnormal.Possible cause: The window stage is not created or destroyed. |

## setDefaultDensityEnabled

```TypeScript
setDefaultDensityEnabled(enabled: boolean): void
```

设置应用主窗口是否使用系统默认Density，子窗和系统窗口会跟随主窗生效。调用此接口前，需先调用WindowStage.loadContent()初始化布局，确保接口调用时序正确。

不调用此接口进行设置，则表示不使用系统默认Density。

不使用系统默认Density时，若调用过setCustomDensity()，则窗口会跟随用户自定义的显示大小变化重新布局，否则跟随系统显示大小变化重新布局。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WindowStage-setDefaultDensityEnabled(enabled: boolean): void--><!--Device-WindowStage-setDefaultDensityEnabled(enabled: boolean): void-End-->

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | boolean | 是 | 是否设置应用使用系统默认Density。true表示使用系统默认Density，窗口不跟随系统显示大小变化重新布局；false表示不使用系统默认Density，窗口跟随系统显示大小变化重新布局。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal.Possible cause: The main window is not created or destroyed. |
| [1300005](../errorcode-window.md#1300005-windowstage异常) | This window stage is abnormal.Possible cause: The window stage is not created or destroyed. |

## setSupportedWindowModes

```TypeScript
setSupportedWindowModes(supportedWindowModes: Array<bundleManager.SupportWindowMode>): Promise<void>
```

设置主窗的窗口支持模式，使用Promise异步回调。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-WindowStage-setSupportedWindowModes(supportedWindowModes: Array<bundleManager.SupportWindowMode>): Promise<void>--><!--Device-WindowStage-setSupportedWindowModes(supportedWindowModes: Array<bundleManager.SupportWindowMode>): Promise<void>-End-->

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| supportedWindowModes | Array&lt;bundleManager.SupportWindowMode&gt; | 是 | 设置主窗的窗口支持模式。<br>- FULL_SCREEN：支持全屏模式。<br>- FLOATING：支持自由悬浮窗口模式。<br>- SPLIT：支持分屏模式。需要配合FULL_SCREEN或FLOATING一起使用，不支持仅配置SPLIT。<br> 注：数组中SupportWindowMode字段取值不应该与该UIAbility对应的[module.json5配置文件][module.json5 file](../../../quick-start/module-configuration-file.md)中[abilities标签](../../../quick-start/module-configuration-file.md#abilities)的supportWindowMode字段取值或者[StartOptions](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-startoptions-startoptions-c.md)的supportWindowModes属性取值冲突。当取值冲突时，最终以该参数设置的窗口支持模式为准。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal. Possible cause:1. The window is not created or destroyed.2. Internal task error. |
| [1300003](../errorcode-window.md#1300003-系统服务工作异常) | This window manager service works abnormally. |

## setSupportedWindowModes

```TypeScript
setSupportedWindowModes(supportedWindowModes: Array<bundleManager.SupportWindowMode>, grayOutMaximizeButton: boolean): Promise<void>
```

设置主窗的窗口支持模式，并提供最大化按钮置灰功能，使用Promise异步回调。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WindowStage-setSupportedWindowModes(supportedWindowModes: Array<bundleManager.SupportWindowMode>, grayOutMaximizeButton: boolean): Promise<void>--><!--Device-WindowStage-setSupportedWindowModes(supportedWindowModes: Array<bundleManager.SupportWindowMode>, grayOutMaximizeButton: boolean): Promise<void>-End-->

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| supportedWindowModes | Array&lt;bundleManager.SupportWindowMode&gt; | 是 | 设置主窗的窗口支持模式。<br>- FULL_SCREEN：支持全屏模式。<br>- FLOATING：支持自由悬浮窗口模式。<br>- SPLIT：支持分屏模式。需要配合FULL_SCREEN或FLOATING一起使用，不支持仅配置SPLIT。<br> 注：数组中SupportWindowMode字段取值不应该与该UIAbility对应的[module.json5配置文件][module.json5 file](../../../quick-start/module-configuration-file.md)中[abilities标签](../../../quick-start/module-configuration-file.md#abilities)的supportWindowMode字段取值或者[StartOptions](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-startoptions-startoptions-c.md)的supportWindowModes属性取值冲突。当取值冲突时，最终以该参数设置的窗口支持模式为准。 |
| grayOutMaximizeButton | boolean | 是 | 是否显示并将主窗口的最大化按钮置灰true表示显示并将主窗口的最大化按钮置灰，此时最大化按钮不可用；false表示不显示主窗口的最大化按钮。此参数配置仅在supportedWindowModes不支持FULL_SCREEN时生效。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.Function setSupportedWindowModes can not work correctly due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal. Possible cause:1. The window is not created or destroyed.2. Internal task error. |
| [1300003](../errorcode-window.md#1300003-系统服务工作异常) | This window manager service works abnormally. |
| [1300016](../errorcode-window.md#1300016-参数校验错误) | Parameter error. Possible cause:1. Invalid parameter range.2. Invalid parameter length.3. Incorrect parameter format. |

## setWindowModal

```TypeScript
setWindowModal(isModal: boolean): Promise<void>
```

Set the application modality of the windowStage.

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-WindowStage-setWindowModal(isModal: boolean): Promise<void>--><!--Device-WindowStage-setWindowModal(isModal: boolean): Promise<void>-End-->

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isModal | boolean | 是 | Enable the window modal if true, otherwise means the opposite. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal. |
| [1300003](../errorcode-window.md#1300003-系统服务工作异常) | This window manager service works abnormally. |
| [1300005](../errorcode-window.md#1300005-windowstage异常) | This window stage is abnormal. Possible cause:The window is not created or destroyed.<br>**适用版本：** 20+ |

## setWindowRectAutoSave

```TypeScript
setWindowRectAutoSave(enabled: boolean): Promise<void>
```

设置是否启用最后关闭的主窗尺寸的记忆功能，使用Promise异步回调。

启用记忆功能后，在同一个UIAbility下，记忆最后关闭的主窗口的尺寸；此主窗口再次启动时，以记忆的尺寸按照规则进行打开。层叠规则：1、当前实例是自由窗口时，打开下一实例窗口层叠时，大小要跟随。2、当前实例是最大化或全屏窗口时，打开下一个实例窗口层叠时，保持最大化。

记忆规则：  
|上一次窗口状态|记忆规则|  
|-------------|-------|  
|自由窗口|保留自由窗口的大小/位置，超出工作区回弹|  
|二分屏窗口|保留二分屏之前自由窗口的大小/位置|  
|最大化窗口|保留最大化|  
|沉浸式窗口|保留沉浸式之前自由窗口的大小/位置|  
|最小化窗口|保留最小化之前自由窗口的大小/位置|

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-WindowStage-setWindowRectAutoSave(enabled: boolean): Promise<void>--><!--Device-WindowStage-setWindowRectAutoSave(enabled: boolean): Promise<void>-End-->

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | boolean | 是 | 设置是否启用主窗尺寸的记忆功能，true为启用，false为不启用。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal.Possible cause: 1. The window is not created or destroyed;2. Internal task error. |
| [1300003](../errorcode-window.md#1300003-系统服务工作异常) | This window manager service works abnormally. |

## setWindowRectAutoSave

```TypeScript
setWindowRectAutoSave(enabled: boolean, isSaveBySpecifiedFlag: boolean): Promise<void>
```

设置是否启用主窗的尺寸记忆功能，使用Promise异步回调。

在同一个UIAbility下，可记忆最后关闭的主窗口尺寸，也可针对每个主窗口尺寸单独进行记忆。只有在UIAbility启动模式为specified，且isSaveBySpecifiedFlag设置为true时，才能针对每个主窗口尺寸进行单独记忆。

启用记忆功能后，记忆主窗口关闭时的尺寸；对应主窗口再次启动时，以记忆的尺寸按照规则进行打开。

记忆规则：  
|上一次窗口状态|记忆规则|  
|-------------|-------|  
|自由窗口|保留自由窗口的大小/位置，超出工作区回弹。|  
|二分屏窗口|保留二分屏之前自由窗口的大小/位置。|  
|最大化窗口|保留最大化。|  
|沉浸式窗口|保留沉浸式之前自由窗口的大小/位置。|  
|最小化窗口|保留最小化之前自由窗口的大小/位置。|

**起始版本：** 17

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本17开始，该接口支持在原子化服务API中使用。

<!--Device-WindowStage-setWindowRectAutoSave(enabled: boolean, isSaveBySpecifiedFlag: boolean): Promise<void>--><!--Device-WindowStage-setWindowRectAutoSave(enabled: boolean, isSaveBySpecifiedFlag: boolean): Promise<void>-End-->

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | boolean | 是 | Enable the window rect auto-save if true, otherwise means the opposite. |
| isSaveBySpecifiedFlag | boolean | 是 | Enable the specifiedFlag if true, otherwise means the opposite. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.Function setWindowRectAutoSave can not work correctly due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal.Possible cause: 1. The window is not created or destroyed;2. Internal task error. |
| [1300003](../errorcode-window.md#1300003-系统服务工作异常) | This window manager service works abnormally. |

