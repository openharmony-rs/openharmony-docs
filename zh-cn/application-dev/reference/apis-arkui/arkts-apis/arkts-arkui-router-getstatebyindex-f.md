# getStateByIndex

## 导入模块

```TypeScript
import { router } from '@kit.ArkUI';
```

<a id="getstatebyindex"></a>
## getStateByIndex

```TypeScript
function getStateByIndex(index: number): RouterState | undefined
```

通过索引值获取对应页面的状态信息。

> **说明：**  
>  
> - 从API version 12开始支持，从API version 18开始废弃，建议使用  
> [getStateByIndex](arkts-arkui-arkui-uicontext-router-c.md#getstatebyindex-1)替代。getStateByIndex需先通过  
> [UIContext](arkts-arkui-uicontext.md)中的  
> [getRouter](docroot://reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getrouter)获取  
> [Router](arkts-arkui-uicontext.md)实例，然后通过该实例进行调用。  
>  
> - 从API version 12开始，可以通过使用[UIContext](arkts-arkui-uicontext.md)中的  
> [getRouter](docroot://reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getrouter)方法获取当前UI上下文关联的  
> [Router](arkts-arkui-uicontext.md)对象。

**起始版本：** 12

**废弃版本：** 18

**替代接口：** [getStateByIndex](arkts-arkui-arkui-uicontext-router-c.md#getstatebyindex-1)

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-router-function getStateByIndex(index: number): RouterState | undefined--><!--Device-router-function getStateByIndex(index: number): RouterState | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | number | 是 | 表示要获取的页面索引。从栈底到栈顶，index从1开始递增。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [RouterState](arkts-arkui-router-routerstate-i.md) | State information about the target page; **undefined** if the specified index does not exist. |

**示例：**

```TypeScript
import { router } from '@kit.ArkUI';

let options: router.RouterState | undefined = router.getStateByIndex(1);
if (options != undefined) {
  console.info('index = ' + options.index);
  console.info('name = ' + options.name);
  console.info('path = ' + options.path);
  console.info(`params = ${JSON.stringify(options.params)}`);
}

```

