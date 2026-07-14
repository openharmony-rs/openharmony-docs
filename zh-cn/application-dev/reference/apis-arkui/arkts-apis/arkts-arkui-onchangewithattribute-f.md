# onChangeWithAttribute

## onChangeWithAttribute

```TypeScript
function onChangeWithAttribute(displayAttributeOption: Array<string>, callback: Callback<number>): void
```

开启显示设备指定属性变化的监听。

**起始版本：** 23

**元服务API：** 从API版本23开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| displayAttributeOption | Array&lt;string&gt; | 是 | 指定需要监听的屏幕属性名称，且仅限于[display属性](../../../../reference/apis-arkui/js-apis-display.md#属性)中包含的属性。 |
| callback | Callback&lt;number&gt; | 是 | 回调函数。返回监听到的屏幕ID，该参数为整数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Function onChangeWithAttribute can not work correctlydue to limited device capabilities. |
| [1400003](../errorcode-display.md#1400003-系统服务工作异常) | This display manager service works abnormally.Possible causes: Internal IPC error. |

**示例：**

```TypeScript
import { Callback } from '@kit.BasicServicesKit';

let attributesChangeCallback: Callback<number> = (data: number) => {
  console.info(`Listening enabled. Data: ${data}`);
};
let attributes: Array<string> = ["rotation", "width"];
display.onChangeWithAttribute(attributes, attributesChangeCallback);

```

