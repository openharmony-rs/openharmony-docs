# queryTouchEvents（系统接口）

## 导入模块

```TypeScript
import { inputMonitor } from '@kit.InputKit';
```

<a id="querytouchevents"></a>
## queryTouchEvents

```TypeScript
function queryTouchEvents(count: number) : Promise<Array<TouchEvent>>
```

查询最近的触屏输入事件，最多支持查询100条事件，从API版本26.0.0开始，最多支持查询60条事件，使用Promise异步回调。

**起始版本：** 20

**需要权限：** ohos.permission.INPUT_MONITORING

<!--Device-inputMonitor-function queryTouchEvents(count: int) : Promise<Array<TouchEvent>>--><!--Device-inputMonitor-function queryTouchEvents(count: int) : Promise<Array<TouchEvent>>-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputMonitor

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| count | number | 是 | 需要查询的触屏输入事件数量，取值范围为0到100的整数。小于0时取值为0、大于100时取值为100。从API版本26.0.0开始，大于60时取值为60。如果实际触屏输入事件只有30个，但该参数取值为50 ，则仅支持查询到30个触屏输入事件。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;TouchEvent&gt;&gt; | Promise对象，返回查询到的触屏输入事件。包含以下有效信息，其余均为无效信息：<br/>- actionTime：触屏输入事件发生的时间，表示系统启动运行至今逝去的微秒数，单位为微秒（μs）。<br/>- [SourceType](arkts-input-multimodalinput-touchevent-sourcetype-e.md)：触摸来源的设备类型。<br/>-[isInject](arkts-input-multimodalinput-touchevent-touchevent-i.md)：表示该触屏输入事件是否为注入事件。<br/>- pressure：压力值，取值范围是[0.0, 1.0]，0.0表示不支持。<br/>- tiltX：相对YZ平面的角度，取值的范围[-90, 90]，其中正值是向右倾斜。<br/>- tiltY：相对XZ平面的角度，取值的范围[-90, 90]，其中正值是向下倾斜。<br/>从API version 23开始，可以额外获取以下有效信息：<br/>- [Action](arkts-input-multimodalinput-touchevent-action-e.md)：触屏输入事件类型。<br/>- screenX：相对于屏幕左上角的X轴坐标，单位为像素，取值范围[0, 屏幕宽度]，向右递增。仅限指定应用获取。<br/>- screenY：相对于屏幕左上角的Y轴坐标，单位为像素，取值范围[0, 屏幕高度]，向下递增。仅限指定应用获取。<br/>从API版本26.0.0开始，最多支持查询60条事件，且不会返回MOVE和PULL_MOVE类型的事件。screenX和screenY不再限制指定应用获取，所有系统应用均可获取。同时可以额外获取以下有效信息：<br/>- screenId：目标屏幕ID。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |

**示例：**

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

