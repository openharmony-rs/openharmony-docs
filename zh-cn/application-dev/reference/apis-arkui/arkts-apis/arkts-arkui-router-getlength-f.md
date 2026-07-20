# getLength

## 导入模块

```TypeScript
import { router } from '@kit.ArkUI';
```

<a id="getlength"></a>
## getLength

```TypeScript
function getLength(): string
```

获取当前在页面栈内的页面数量。

> **说明：**  
>  
> - 从API version 8开始支持，从API version 18开始废弃，建议使用[getLength](arkts-arkui-arkui-uicontext-router-c.md#getlength-1)替代。  
> getLength需先通过[UIContext](arkts-arkui-uicontext.md)中的  
> [getRouter](docroot://reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getrouter)获取  
> [Router](arkts-arkui-uicontext.md)实例，然后通过该实例进行调用。  
>  
> - 从API version 10开始，可以通过使用[UIContext](arkts-arkui-uicontext.md)中的  
> [getRouter](docroot://reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getrouter)方法获取当前UI上下文关联的  
> [Router](arkts-arkui-uicontext.md)对象。

**起始版本：** 8

**废弃版本：** 18

**替代接口：** [getLength](arkts-arkui-arkui-uicontext-router-c.md#getlength-1)

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-router-function getLength(): string--><!--Device-router-function getLength(): string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 页面数量，页面栈支持最大数值是32。 |

**示例：**

```TypeScript
let size = this.getUIContext().getRouter().getLength();
console.info('pages stack size = ' + size);

```

