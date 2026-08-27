# GetFormRectInfoCallback（系统接口）

```TypeScript
type GetFormRectInfoCallback = (formId: string) => Promise<formInfo.Rect>
```

卡片位置、尺寸查询回调。使用Promise异步回调。

**起始版本：** 20

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| formId | string | 是 | 卡片Id。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[formInfo.Rect](arkts-form-forminfo-rect-i.md)&gt; | Promise对象，返回卡片相对屏幕左上角的位置信息和卡片尺寸信息。 |

**示例**

```TypeScript
import { formInfo } from '@kit.FormKit';

// 卡片使用方需要对查询请求进行处理，计算并返回卡片尺寸、位置信息
let getFormRectInfoCallback: formInfo.GetFormRectInfoCallback =
  (formId: string): Promise<formInfo.Rect> => {
    return new Promise<formInfo.Rect>((resolve: (value: formInfo.Rect) => void) => {
      console.info(`formId is ${formId}`);
      let formRect: formInfo.Rect = {
        left: 0,
        top: 0,
        width: 0,
        height: 0
      };
      resolve(formRect);
    })
  };
```
