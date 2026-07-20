# getStateByUrl

## 导入模块

```TypeScript
import { router } from '@kit.ArkUI';
```

<a id="getstatebyurl"></a>
## getStateByUrl

```TypeScript
function getStateByUrl(url: string): Array<RouterState>
```

通过url获取对应页面的状态信息。

> **说明：**  
>  
> - 从API version 12开始支持，从API version 18开始废弃，建议使用[getStateByUrl](arkts-arkui-arkui-uicontext-router-c.md#getstatebyurl-1)替  
> 代。getStateByUrl需先通过[UIContext](arkts-arkui-uicontext.md)中的  
> [getRouter](docroot://reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getrouter)获取  
> [Router](arkts-arkui-uicontext.md)实例，然后通过该实例进行调用。  
>  
> - 从API version 12开始，可以通过使用[UIContext](arkts-arkui-uicontext.md)中的  
> [getRouter](docroot://reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getrouter)方法获取当前UI上下文关联的  
> [Router](arkts-arkui-uicontext.md)对象。

**起始版本：** 12

**废弃版本：** 18

**替代接口：** [getStateByUrl](arkts-arkui-arkui-uicontext-router-c.md#getstatebyurl-1)

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-router-function getStateByUrl(url: string): Array<RouterState>--><!--Device-router-function getStateByUrl(url: string): Array<RouterState>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| url | string | 是 | 表示要获取对应页面信息的url。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;RouterState&gt; | 页面状态信息。 |

**示例：**

```TypeScript
import { router } from '@kit.ArkUI';

let options: Array<router.RouterState> = router.getStateByUrl('pages/index');
for (let i: number = 0; i < options.length; i++) {
  console.info('index = ' + options[i].index);
  console.info('name = ' + options[i].name);
  console.info('path = ' + options[i].path);
  console.info('params = ' + options[i].params);
}

```

