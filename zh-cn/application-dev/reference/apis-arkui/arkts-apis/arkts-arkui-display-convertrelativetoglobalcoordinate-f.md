# convertRelativeToGlobalCoordinate

## 导入模块

```TypeScript
import { display } from '@kit.ArkUI';
```

<a id="convertrelativetoglobalcoordinate"></a>
## convertRelativeToGlobalCoordinate

```TypeScript
function convertRelativeToGlobalCoordinate(relativePosition: RelativePosition): Position
```

将指定屏幕左上角为原点的相对坐标转换成主屏左上角为原点的全局坐标，仅支持主屏和扩展屏的坐标转换。

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-display-function convertRelativeToGlobalCoordinate(relativePosition: RelativePosition): Position--><!--Device-display-function convertRelativeToGlobalCoordinate(relativePosition: RelativePosition): Position-End-->

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| relativePosition | [RelativePosition](arkts-arkui-display-relativeposition-i.md) | 是 | 需要转化为全局坐标的相对坐标。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Position](arkts-arkui-display-position-i.md) | 返回相对于主屏左上角的全局坐标。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1400003](../errorcode-display.md#1400003-系统服务工作异常) | This display manager service works abnormally. |
| [1400004](../errorcode-display.md#1400004-参数异常) | Parameter error. Possible cause: 1. Invalid parameter range. |

**示例：**

```TypeScript
// 定义需要转换的相对坐标
let relativePosition: display.RelativePosition = {
  displayId: 0,
  position: {
    x: 100,
    y: 200
  }
};

try {
   // 将相对坐标转换为全局坐标
  let position: display.Position = display.convertRelativeToGlobalCoordinate(relativePosition);
  console.info(`The global coordinate is ${position.x}, ${position.y}`)
} catch (exception) {
  console.error(`Failed to convert the relative coordinate to the global coordinate. Code: ${exception.code}, message: ${exception.message}`);
}

```

