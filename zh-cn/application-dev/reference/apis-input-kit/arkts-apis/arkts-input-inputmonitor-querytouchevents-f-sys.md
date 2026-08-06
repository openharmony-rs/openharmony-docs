# queryTouchEvents（系统接口）

## queryTouchEvents

```TypeScript
function queryTouchEvents(count: int) : Promise<Array<TouchEvent>>
```

查询最近的触屏输入事件，最多支持查询100条事件，从API版本26.0.0开始，最多支持查询60条事件，使用Promise异步回调。

**起始版本：** 20

**ArkTS模式：** ArkTS-Dyn起始版本为20；ArkTS-Sta起始版本为23。

**需要权限：** ohos.permission.INPUT_MONITORING

<!--Device-inputMonitor-function queryTouchEvents(count: int) : Promise<Array<TouchEvent>>--><!--Device-inputMonitor-function queryTouchEvents(count: int) : Promise<Array<TouchEvent>>-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputMonitor

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| count | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 需要查询的触屏输入事件数量，取值范围为0到100的整数。小于0时取值为0、大于100时取值为100。从API版本26.0.0开始，大于60时取值为60。如果实际触屏输入事件只有30个，但该参数取值为50 ，则仅支持查询到30个触屏输入事件。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;\_\_\_MD\_LINK\_USD\_0\_\_\_&gt;&gt; | Promise对象，返回查询到的触屏输入事件。包含以下有效信息，其余均为无效信息：\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_- actionTime：触屏输入事件发生的时间，表示系统 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |

**示例：**

ArkTS-Dyn示例：

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

ArkTS-Sta示例：

```TypeScript
import { Entry, Text, RelativeContainer, Component } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';
import { inputMonitor, TouchEvent } from '@kit.InputKit'

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            // 查询触屏事件数量
            inputMonitor.queryTouchEvents(10).then((events: Array<TouchEvent>) => {
              console.info(`Succeeded in querying touch events, events=${events}.`);
            });
          } catch(error) {
            const code = (error as BusinessError).code;
            const message = (error as BusinessError).message;
            console.error(`Failed to query touch events, Code: ${code}, message: ${message}.`);
          }
        })
    }
  }
}
```

