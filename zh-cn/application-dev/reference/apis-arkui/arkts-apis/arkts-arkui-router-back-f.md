# back

## 导入模块

```TypeScript
import { router } from '@kit.ArkUI';
```

## back

```TypeScript
function back(options?: RouterOptions): void
```

返回上一页面或指定的页面，会删除当前页面与指定页面之间的所有页面。

> **说明：**  
>  
> - 从API version 8开始支持，从API version 18开始废弃，建议使用  
> [back](arkts-arkui-arkui-uicontext-router-c.md#back-1)替代。back需先通过  
> [UIContext](arkts-arkui-uicontext.md)中的  
> [getRouter](../../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getrouter)获取  
> [Router](arkts-arkui-uicontext.md)实例，然后通过该实例进行调用。  
>  
> - 从API version 10开始，可以通过使用[UIContext](arkts-arkui-uicontext.md)中的  
> [getRouter](../../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getrouter)方法获取当前UI上下文关联的  
> [Router](arkts-arkui-uicontext.md)对象。

**起始版本：** 8

**废弃版本：** 18

**替代接口：** back(options?:

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-router-function back(options?: RouterOptions): void--><!--Device-router-function back(options?: RouterOptions): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [RouterOptions](arkts-arkui-router-routeroptions-i.md) | 否 | 返回页面描述信息，其中参数url指路由跳转时会返回到指定url的界面，如果页面栈上没有url页面，则不响应该情况。如果url未设置，则返回上一页，页面不会重新构建，页面栈里面的page不会回收，出栈后会被回收。back是返回接口，url设置为特殊值"/"不生效。如果是用命名路由的方式跳转，传入的url需是命名路由的名称。 |

**示例：**

```TypeScript
this.getUIContext().getRouter().back({ url: 'pages/detail' });

```


## back

```TypeScript
function back(index: number, params?: Object): void
```

返回指定的页面，会删除当前页面与指定页面之间的所有页面。

> **说明：**  
>  
> - 从API version 12开始支持，从API version 18开始废弃，建议使用  
> [back](arkts-arkui-arkui-uicontext-router-c.md#back-2)替代。back需先通过  
> [UIContext](arkts-arkui-uicontext.md)中的  
> [getRouter](../../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getrouter)获取  
> [Router](arkts-arkui-uicontext.md)实例，然后通过该实例进行调用。  
>  
> - 从API version 12开始，可以通过使用[UIContext](arkts-arkui-uicontext.md)中的  
> [getRouter](../../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getrouter)方法获取当前UI上下文关联的  
> [Router](arkts-arkui-uicontext.md)对象。

**起始版本：** 12

**废弃版本：** 18

**替代接口：** back(index:

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-router-function back(index: number, params?: Object): void--><!--Device-router-function back(index: number, params?: Object): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | number | 是 | 跳转目标页面的索引值。 从栈底到栈顶，index从1开始递增。 |
| params | Object | 否 | 页面返回时携带的参数。 |

**示例：**

```TypeScript
this.getUIContext().getRouter().back(1);

```

```TypeScript
this.getUIContext().getRouter().back(1, { info: '来自Home页' }); // 携带参数返回

```

