# queryTouchEvents（系统接口）

## 导入模块

```TypeScript
```

## queryTouchEvents

```TypeScript
function queryTouchEvents(count: number) : Promise<Array<TouchEvent>>
```

查询最近的触屏输入事件，最多支持查询100条事件，从API版本26.0.0开始，最多支持查询60条事件，使用Promise异步回调。

**起始版本：** 20

**需要权限：** ohos.permission.INPUT_MONITORING

**系统能力：** SystemCapability.MultimodalInput.Input.InputMonitor

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| count | number | 是 | 需要查询的触屏输入事件数量，取值范围为[0, 100]的整数。小于0时取值为0、大于100时取值为100。从API版本26.0.0开始，大于60时取值为60。如果实际触屏输入事件只有30个， 但该参数取值为50 ，则仅支持查询到30个触屏输入事件。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;[TouchEvent](arkts-input-multimodalinput-touchevent-touchevent-i.md)&gt;&gt; | Promise对象，返回查询到的触屏输入事件。包含以下有效信息，其余均为无效信息： |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |

**示例**

```TypeScript
import { inputMonitor, TouchEvent } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // 查询触屏事件数量
  inputMonitor.queryTouchEvents(10).then((events: Array<TouchEvent>) => {
    events.forEach((event, index) => {
      console.info(`Succeeded in querying touch event ${index}, actionTime=${event.actionTime}, sourceType=${event.sourceType}.`);
    });
  }).catch((error: BusinessError) => {
    console.error(`Failed to query touch events promise, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
  });
} catch (error) {
  const code = (error as BusinessError).code;
  const message = (error as BusinessError).message;
  console.error(`Failed to query touch events, Code: ${code}, message: ${message}.`);
}
```
