# getState

## 导入模块

```TypeScript
import { router } from '@kit.ArkUI';
```

## getState

```TypeScript
function getState(): RouterState
```

获取栈顶页面的状态信息。

> **说明：**  
>  
> - 从API version 8开始支持，从API version 18开始废弃，建议使用[getState](arkts-arkui-arkui-uicontext-router-c.md#getstate-1)替代。getLength需  
> 先通过[UIContext](arkts-arkui-uicontext.md)中的  
> [getRouter](../../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getrouter)获取  
> [Router](arkts-arkui-uicontext.md)实例，然后通过该实例进行调用。  
>  
> - 从API version 10开始，可以通过使用[UIContext](arkts-arkui-uicontext.md)中的  
> [getRouter](../../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getrouter)方法获取当前UI上下文关联的  
> [Router](arkts-arkui-uicontext.md)对象。

**起始版本：** 8

**废弃版本：** 18

**替代接口：** [getState](arkts-arkui-arkui-uicontext-router-c.md#getstate-1)

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-router-function getState(): RouterState--><!--Device-router-function getState(): RouterState-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [RouterState](arkts-arkui-router-routerstate-i.md) | 页面状态信息。 |

**示例：**

```TypeScript
let page = this.getUIContext().getRouter().getState();
console.info('current index = ' + page.index);
console.info('current name = ' + page.name);
console.info('current path = ' + page.path);

```

