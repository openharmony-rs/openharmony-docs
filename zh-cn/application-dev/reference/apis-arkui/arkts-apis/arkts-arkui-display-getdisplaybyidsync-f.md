# getDisplayByIdSync

## 导入模块

```TypeScript
import { display } from '@kit.ArkUI';
```

<a id="getdisplaybyidsync"></a>
## getDisplayByIdSync

```TypeScript
function getDisplayByIdSync(displayId: number): Display
```

根据displayId获取对应的Display对象。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-display-function getDisplayByIdSync(displayId: long): Display--><!--Device-display-function getDisplayByIdSync(displayId: long): Display-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| displayId | number | 是 | 屏幕ID。该参数仅支持整数输入，该参数大于等于0。需要确保displayId准确才能成功获取到对应结果。可以通过[WindowProperties](arkts-arkui-window-windowproperties-i.md)的displayId属性获取到准确的displayId作为入参。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Display](arkts-arkui-display-display-i.md) | 返回displayId对应的Display对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.2. Incorrect parameter types.3. Parameter verification failed. |
| [1400003](../errorcode-display.md#1400003-系统服务工作异常) | This display manager service works abnormally. Possible causes:Display is null, display id corresponding display does not exist. |

**示例：**

```TypeScript
let displayClass: display.Display | null = null;

try {
  // 可以通过WindowProperties的displayId属性获取到准确的displayId作为入参
  let displayId = 0; 
  displayClass = display.getDisplayByIdSync(displayId);
} catch (exception) {
  console.error(`Failed to get display. Code: ${exception.code}, message: ${exception.message}`);
}

```

