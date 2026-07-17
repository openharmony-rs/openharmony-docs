# create

## 导入模块

```TypeScript
import { sendableColorSpaceManager } from '@kit.ArkGraphics2D';
```

## create

```TypeScript
function create(colorSpaceName: colorSpaceManager.ColorSpace): ColorSpaceManager
```

创建标准可共享的色彩管理。

**起始版本：** 12

<!--Device-sendableColorSpaceManager-function create(colorSpaceName: colorSpaceManager.ColorSpace): ColorSpaceManager--><!--Device-sendableColorSpaceManager-function create(colorSpaceName: colorSpaceManager.ColorSpace): ColorSpaceManager-End-->

**系统能力：** SystemCapability.Graphic.Graphic2D.ColorManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| colorSpaceName | colorSpaceManager.ColorSpace | 是 | 标准色域类型枚举值。<br>UNKNOWN与CUSTOM不可用于直接创建色域对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ColorSpaceManager](arkts-arkgraphics2d-sendablecolorspacemanager-colorspacemanager-i.md) | 返回当前创建的可共享的色彩管理实例。<br>该实例继承ISendable，可以在ArkTS并发实例间（包括主线程、TaskPool&Worker工作线程）传递，传递的行为是引用传递，参考[Sendable使用场景](../../../../arkts-utils/sendable-guide.md)。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible cause: 1.Incorrect parameter type.2.Parameter verification failed. |
| [18600001](../errorcode-colorspace-manager.md#18600001-参数值异常) | The parameter value is abnormal. |

**示例：**

```TypeScript
import { colorSpaceManager, sendableColorSpaceManager } from '@kit.ArkGraphics2D';
let colorSpace: sendableColorSpaceManager.ColorSpaceManager;
// 创建标准SRGB色域的色彩管理实例
colorSpace = sendableColorSpaceManager.create(colorSpaceManager.ColorSpace.SRGB);

```


## create

```TypeScript
function create(primaries: colorSpaceManager.ColorSpacePrimaries, gamma: number): ColorSpaceManager
```

创建用户自定义可共享的色彩管理实例。

**起始版本：** 12

<!--Device-sendableColorSpaceManager-function create(primaries: colorSpaceManager.ColorSpacePrimaries, gamma: number): ColorSpaceManager--><!--Device-sendableColorSpaceManager-function create(primaries: colorSpaceManager.ColorSpacePrimaries, gamma: number): ColorSpaceManager-End-->

**系统能力：** SystemCapability.Graphic.Graphic2D.ColorManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| primaries | colorSpaceManager.ColorSpacePrimaries | 是 | 色域标准三原色。 |
| gamma | number | 是 | 色域gamma值，取值为大于0的浮点数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ColorSpaceManager](arkts-arkgraphics2d-sendablecolorspacemanager-colorspacemanager-i.md) | 返回当前创建的可共享的色彩管理实例。<br>色域类型定义为[colorSpaceManager.ColorSpace](arkts-arkgraphics2d-colorspacemanager-colorspace-e.md)枚举值`CUSTOM`。<br>该实例继承ISendable，可以在ArkTS并发实例间（包括主线程、TaskPool&Worker工作线程）传递，传递的行为是引用传递，参考[Sendable使用场景](../../../../arkts-utils/sendable-guide.md)。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible cause: 1.Incorrect parameter type.2.Parameter verification failed. |
| [18600001](../errorcode-colorspace-manager.md#18600001-参数值异常) | The parameter value is abnormal. |

**示例：**

```TypeScript
import { colorSpaceManager, sendableColorSpaceManager } from '@kit.ArkGraphics2D';
let colorSpace: sendableColorSpaceManager.ColorSpaceManager;
// 定义色域标准三原色参数
let primaries: colorSpaceManager.ColorSpacePrimaries = {
  redX: 0.1,
  redY: 0.1,
  greenX: 0.2,
  greenY: 0.2,
  blueX: 0.3,
  blueY: 0.3,
  whitePointX: 0.4,
  whitePointY: 0.4
};
// 定义色域gamma值
let gamma: number = 2.2;
// 创建自定义可共享的色彩管理实例
colorSpace = sendableColorSpaceManager.create(primaries, gamma);

```

