# create

## 导入模块

```TypeScript
import { colorSpaceManager } from '@kit.ArkGraphics2D';
```

## create

```TypeScript
function create(colorSpaceName: ColorSpace): ColorSpaceManager
```

创建标准色域对象。

**起始版本：** 9

<!--Device-colorSpaceManager-function create(colorSpaceName: ColorSpace): ColorSpaceManager--><!--Device-colorSpaceManager-function create(colorSpaceName: ColorSpace): ColorSpaceManager-End-->

**系统能力：** SystemCapability.Graphic.Graphic2D.ColorManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| colorSpaceName | [ColorSpace](../../apis-arkui/arkts-apis/arkts-arkui-window-colorspace-e.md) | 是 | 标准色域类型枚举值。<br>UNKNOWN与CUSTOM不可用于直接创建色域对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ColorSpaceManager](arkts-arkgraphics2d-sendablecolorspacemanager-colorspacemanager-i.md) | 返回当前创建的色域对象实例。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible cause: 1.Incorrect parameter type.2.Parameter verification failed. |
| [18600001](../errorcode-colorspace-manager.md#18600001-参数值异常) | The parameter value is abnormal. |

**示例：**

```TypeScript
try {
  // 创建标准SRGB色域的色彩管理实例
  let colorSpace = colorSpaceManager.create(colorSpaceManager.ColorSpace.SRGB);
} catch (err) {
  console.error(`Failed to create SRGB colorSpace. Code: ${err.code}, message: ${err.message}`);
}

```


## create

```TypeScript
function create(primaries: ColorSpacePrimaries, gamma: number): ColorSpaceManager
```

创建用户自定义色域对象。

**起始版本：** 9

<!--Device-colorSpaceManager-function create(primaries: ColorSpacePrimaries, gamma: double): ColorSpaceManager--><!--Device-colorSpaceManager-function create(primaries: ColorSpacePrimaries, gamma: double): ColorSpaceManager-End-->

**系统能力：** SystemCapability.Graphic.Graphic2D.ColorManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| primaries | [ColorSpacePrimaries](arkts-arkgraphics2d-colorspacemanager-colorspaceprimaries-i.md) | 是 | 色域标准三原色。 |
| gamma | number | 是 | 色域gamma值，取值为大于0的浮点数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ColorSpaceManager](arkts-arkgraphics2d-sendablecolorspacemanager-colorspacemanager-i.md) | 返回当前创建的色域对象实例。<br>色域类型定义为[ColorSpace](arkts-arkgraphics2d-colorspacemanager-colorspace-e.md)枚举值`CUSTOM`。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible cause: 1.Incorrect parameter type.2.Parameter verification failed. |
| [18600001](../errorcode-colorspace-manager.md#18600001-参数值异常) | The parameter value is abnormal. |

**示例：**

```TypeScript
try {
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
  let gamma = 2.2;
  // 创建自定义色域对象
  let colorSpace = colorSpaceManager.create(primaries, gamma);
} catch (err) {
  console.error(`Failed to create colorSpace with customized primaries and gamma. Code: ${err.code}, message: ${err.message}`);
}

```

