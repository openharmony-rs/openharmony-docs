# ColorSpaceManager

当前色域对象实例。 下列API示例中都需先使用[create()]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_获取到ColorSpaceManager实例，再通过此实例调用对 应方法。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-colorSpaceManager-interface ColorSpaceManager--><!--Device-colorSpaceManager-interface ColorSpaceManager-End-->

**系统能力：** SystemCapability.Graphic.Graphic2D.ColorManager.Core

## getColorSpaceName

```TypeScript
getColorSpaceName(): ColorSpace
```

获取色域类型。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-ColorSpaceManager-getColorSpaceName(): ColorSpace--><!--Device-ColorSpaceManager-getColorSpaceName(): ColorSpace-End-->

**系统能力：** SystemCapability.Graphic.Graphic2D.ColorManager.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 返回色域类型枚举值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [18600001](../errorcode-colorspace-manager.md#18600001-参数值异常) | The parameter value is abnormal.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 9 - 22 |

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

## getGamma

ArkTS-Dyn:
```TypeScript
getGamma(): number
```

ArkTS-Sta:
```TypeScript
getGamma(): double
```

获取色域gamma值。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-ColorSpaceManager-getGamma(): double--><!--Device-ColorSpaceManager-getGamma(): double-End-->

**系统能力：** SystemCapability.Graphic.Graphic2D.ColorManager.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：double | 返回色域gamma值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [18600001](../errorcode-colorspace-manager.md#18600001-参数值异常) | The parameter value is abnormal.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 9 - 22 |

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

## getWhitePoint

ArkTS-Dyn:
```TypeScript
getWhitePoint(): Array<number>
```

ArkTS-Sta:
```TypeScript
getWhitePoint(): Array<double>
```

获取色域白点值。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-ColorSpaceManager-getWhitePoint(): Array<double>--><!--Device-ColorSpaceManager-getWhitePoint(): Array<double>-End-->

**系统能力：** SystemCapability.Graphic.Graphic2D.ColorManager.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArkTS-Dyn: Array&lt;number&gt;  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：Array&lt;double&gt; | 返回色域白点值[x, y]。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [18600001](../errorcode-colorspace-manager.md#18600001-参数值异常) | The parameter value is abnormal.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 9 - 22 |

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

