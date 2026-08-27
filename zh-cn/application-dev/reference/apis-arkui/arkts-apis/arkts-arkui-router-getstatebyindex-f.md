# getStateByIndex

## 导入模块

```TypeScript
import { router } from '@kit.ArkUI';
```

## getStateByIndex

```TypeScript
function getStateByIndex(index: number): RouterState | undefined
```

通过索引值获取对应页面的状态信息。

> **说明：**
> 
> - 从API version 12开始支持，从API version 18开始废弃，建议使用
> [getStateByIndex](arkts-arkui-arkui-uicontext-router-c.md#getstatebyindex)替代。getStateByIndex需先通过
> [UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md)中的
> [getRouter](arkts-arkui-arkui-uicontext-uicontext-c.md#getrouter)获取
> [Router](arkts-arkui-arkui-uicontext-uicontext-c.md)实例，然后通过该实例进行调用。
> 
> - 从API version 12开始，可以通过使用[UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md)中的
> [getRouter](arkts-arkui-arkui-uicontext-uicontext-c.md#getrouter)方法获取当前UI上下文关联的
> [Router](arkts-arkui-arkui-uicontext-uicontext-c.md)对象。

**起始版本：** 12

**废弃版本：** 18

**替代接口：** [getStateByIndex](arkts-arkui-arkui-uicontext-router-c.md#getstatebyindex)

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | number | 是 | 表示要获取的页面索引，取值范围[1, 页面栈大小]，页面栈最大数量为32。从栈底到栈顶，index从1开始递增。索引不存在时返回undefined。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| RouterState \| undefined | 返回对应索引页面的状态信息，包含页面索引、名称、路径和参数。索引不存在时返回undefined。 |

**示例**

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
