# getCurrentFoldCreaseRegion

## 导入模块

```TypeScript
import { display } from '@kit.ArkUI';
```

## getCurrentFoldCreaseRegion

```TypeScript
function getCurrentFoldCreaseRegion(): FoldCreaseRegion
```

在当前显示模式下获取折叠折痕区域。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-display-function getCurrentFoldCreaseRegion(): FoldCreaseRegion--><!--Device-display-function getCurrentFoldCreaseRegion(): FoldCreaseRegion-End-->

**系统能力：** SystemCapability.Window.SessionManager

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [FoldCreaseRegion](arkts-arkui-display-foldcreaseregion-i.md) | FoldCreaseRegion对象，返回设备在当前显示模式下的折叠折痕区域。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1400003](../errorcode-display.md#1400003-系统服务工作异常) | This display manager service works abnormally. |

**示例：**

```TypeScript
let data: display.FoldCreaseRegion = display.getCurrentFoldCreaseRegion();
console.info(`Succeeded in obtaining current fold crease region. Data: ${JSON.stringify(data)}`);

```

