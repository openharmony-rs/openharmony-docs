# ColorSpaceManager

当前色域对象实例。下列API示例中都需先使用[create()](arkts-arkgraphics2d-colorspacemanager-create-f.md#create-1)获取到ColorSpaceManager实例，再通过此实例调用对应方法。

**起始版本：** 9

<!--Device-colorSpaceManager-interface ColorSpaceManager--><!--Device-colorSpaceManager-interface ColorSpaceManager-End-->

**系统能力：** SystemCapability.Graphic.Graphic2D.ColorManager.Core

## 导入模块

```TypeScript
import { colorSpaceManager } from '@kit.ArkGraphics2D';
```

<a id="getcolorspacename"></a>
## getColorSpaceName

```TypeScript
getColorSpaceName(): ColorSpace
```

获取色域类型。

**起始版本：** 9

<!--Device-ColorSpaceManager-getColorSpaceName(): ColorSpace--><!--Device-ColorSpaceManager-getColorSpaceName(): ColorSpace-End-->

**系统能力：** SystemCapability.Graphic.Graphic2D.ColorManager.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ColorSpace](../../apis-arkui/arkts-apis/arkts-arkui-window-colorspace-e.md) | 返回色域类型枚举值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [18600001](../errorcode-colorspace-manager.md#18600001-参数值异常) | The parameter value is abnormal.<br>**适用版本：** 9 - 22 |

**示例：**

```TypeScript
try {
  // 获取色域类型
  let spaceName = colorSpace.getColorSpaceName();
  console.info(`spaceName: ` + spaceName.toString());
} catch (err) {
  console.error(`Failed to get colorSpace's name. Code: ${err.code}, message: ${err.message}`);
}

```

<a id="getgamma"></a>
## getGamma

```TypeScript
getGamma(): number
```

获取色域gamma值。

**起始版本：** 9

<!--Device-ColorSpaceManager-getGamma(): double--><!--Device-ColorSpaceManager-getGamma(): double-End-->

**系统能力：** SystemCapability.Graphic.Graphic2D.ColorManager.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回色域gamma值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [18600001](../errorcode-colorspace-manager.md#18600001-参数值异常) | The parameter value is abnormal.<br>**适用版本：** 9 - 22 |

**示例：**

```TypeScript
try {
  // 获取色域gamma值
  let gamma = colorSpace.getGamma();
  console.info(`gamma: ` + gamma.toString());
} catch (err) {
  console.error(`Failed to get gamma. Code: ${err.code}, message: ${err.message}`);
}

```

<a id="getwhitepoint"></a>
## getWhitePoint

```TypeScript
getWhitePoint(): Array<number>
```

获取色域白点值。

**起始版本：** 9

<!--Device-ColorSpaceManager-getWhitePoint(): Array<double>--><!--Device-ColorSpaceManager-getWhitePoint(): Array<double>-End-->

**系统能力：** SystemCapability.Graphic.Graphic2D.ColorManager.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;number&gt; | 返回色域白点值[x, y]。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [18600001](../errorcode-colorspace-manager.md#18600001-参数值异常) | The parameter value is abnormal.<br>**适用版本：** 9 - 22 |

**示例：**

```TypeScript
try {
  // 获取色域白点值
  let point = colorSpace.getWhitePoint();
  console.info(`point: ` + point.toString());
} catch (err) {
  console.error(`Failed to get white point. Code: ${err.code}, message: ${err.message}`);
}

```

