# Region

区域对象，用于描述所绘制图形的区域信息。
> **说明：**  
>  
> - 本Class首批接口从API version 12开始支持。  
>  
> - 本模块使用屏幕物理像素单位px。  
>  
> - 本模块为单线程模型策略，需要调用方自行管理线程安全和上下文状态的切换。

**起始版本：** 12

<!--Device-drawing-class Region--><!--Device-drawing-class Region-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## 导入模块

```TypeScript
import { drawing } from '@kit.ArkGraphics2D';
```

## constructor

```TypeScript
constructor()
```

构造一个区域对象。

**起始版本：** 20

<!--Device-Region-constructor()--><!--Device-Region-constructor()-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## constructor

```TypeScript
constructor(region: Region)
```

拷贝一个区域对象。

**起始版本：** 20

<!--Device-Region-constructor(region: Region)--><!--Device-Region-constructor(region: Region)-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| region | [Region](../../apis-image-kit/arkts-apis/arkts-image-image-region-i.md) | 是 | 用于拷贝的区域。 |

## constructor

```TypeScript
constructor(left: number, top: number, right: number, bottom: number)
```

构造矩形区域。

**起始版本：** 20

<!--Device-Region-constructor(left: int, top: int, right: int, bottom: int)--><!--Device-Region-constructor(left: int, top: int, right: int, bottom: int)-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| left | number | 是 | 矩形区域的左侧位置（矩形左上角横坐标）。该参数必须为整数。0表示坐标原点，负数表示位于坐标原点左侧，正数表示位于坐标原点右侧。 |
| top | number | 是 | 矩形区域的顶部位置（矩形左上角纵坐标）。该参数必须为整数。0表示坐标原点，负数表示位于坐标原点上侧，正数表示位于坐标原点下侧。 |
| right | number | 是 | 矩形区域的右侧位置（矩形右下角横坐标）。该参数必须为整数。0表示坐标原点，负数表示位于坐标原点左侧，正数表示位于坐标原点右侧。 |
| bottom | number | 是 | 矩形区域的底部位置（矩形右下角纵坐标）。该参数必须为整数。0表示坐标原点，负数表示位于坐标原点上侧，正数表示位于坐标原点下侧。 |

## getBoundaryPath

```TypeScript
getBoundaryPath(): Path
```

返回一个新路径，该路径取自当前区域的边界。

**起始版本：** 20

<!--Device-Region-getBoundaryPath(): Path--><!--Device-Region-getBoundaryPath(): Path-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Path](arkts-arkgraphics2d-drawing-path-c.md) | 返回当前区域边界的路径。 |

## getBounds

```TypeScript
getBounds(): common2D.Rect
```

获取区域的边界。

**起始版本：** 20

<!--Device-Region-getBounds(): common2D.Rect--><!--Device-Region-getBounds(): common2D.Rect-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| common2D.Rect | Bounding rectangle of this region. |

## isComplex

```TypeScript
isComplex(): boolean
```

判断当前区域是否包含多个矩形。

**起始版本：** 20

<!--Device-Region-isComplex(): boolean--><!--Device-Region-isComplex(): boolean-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回当前区域是否包含多个矩形的结果。true表示当前区域包含多个矩形，false表示当前区域不包含多个矩形。 |

## isEmpty

```TypeScript
isEmpty(): boolean
```

判断当前区域是否为空。

**起始版本：** 20

<!--Device-Region-isEmpty(): boolean--><!--Device-Region-isEmpty(): boolean-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回当前区域是否为空。true表示当前区域为空，false表示当前区域不为空。 |

## isEqual

```TypeScript
isEqual(other: Region): boolean
```

用于判断其他区域是否与当前区域相等。

**起始版本：** 20

<!--Device-Region-isEqual(other: Region): boolean--><!--Device-Region-isEqual(other: Region): boolean-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| other | [Region](../../apis-image-kit/arkts-apis/arkts-image-image-region-i.md) | 是 | 区域对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回其他区域是否与当前区域相等的结果。true表示相等，false表示不相等。 |

## isPointContained

```TypeScript
isPointContained(x: number, y:number): boolean
```

判断测试点是否在区域内。

**起始版本：** 12

<!--Device-Region-isPointContained(x: int, y:int): boolean--><!--Device-Region-isPointContained(x: int, y:int): boolean-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| x | number | 是 | 测试点的x轴坐标。该参数必须为整数。如果输入的数字包含小数部分，小数部分将被舍去。 |
| y | number | 是 | 测试点的y轴坐标。该参数必须为整数。如果输入的数字包含小数部分，小数部分将被舍去。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回测试点是否在区域内的结果。true表示测试点在区域内，false表示测试点不在区域内。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types. |

## isRect

```TypeScript
isRect(): boolean
```

判断当前区域是否等同于单个矩形。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Region-isRect(): boolean--><!--Device-Region-isRect(): boolean-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回当前区域是否等同于单个矩形的结果。true表示当前区域等同于单个矩形，false表示当前区域不等同于单个矩形。 |

## isRegionContained

```TypeScript
isRegionContained(other: Region): boolean
```

判断其他区域是否在当前区域内。

**起始版本：** 12

<!--Device-Region-isRegionContained(other: Region): boolean--><!--Device-Region-isRegionContained(other: Region): boolean-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| other | [Region](../../apis-image-kit/arkts-apis/arkts-image-image-region-i.md) | 是 | 区域对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回其他区域是否在当前区域内的结果。true表示其他区域在当前区域内，false表示其他区域不在当前区域内。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types. |

## offset

```TypeScript
offset(dx: number, dy: number): void
```

对区域进行平移。

**起始版本：** 20

<!--Device-Region-offset(dx: int, dy: int): void--><!--Device-Region-offset(dx: int, dy: int): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| dx | number | 是 | x轴方向平移量，正数往x轴正方向平移，负数往x轴负方向平移，该参数为整数。 |
| dy | number | 是 | y轴方向平移量，正数往y轴正方向平移，负数往y轴负方向平移，该参数为整数。 |

## op

```TypeScript
op(region: Region, regionOp: RegionOp): boolean
```

将当前区域与指定区域进行运算，并替换为运算结果。

**起始版本：** 12

<!--Device-Region-op(region: Region, regionOp: RegionOp): boolean--><!--Device-Region-op(region: Region, regionOp: RegionOp): boolean-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| region | [Region](../../apis-image-kit/arkts-apis/arkts-image-image-region-i.md) | 是 | 区域对象。 |
| regionOp | [RegionOp](arkts-arkgraphics2d-drawing-regionop-e.md) | 是 | 区域合并操作类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回区域运算结果是否成功替换当前区域。true表示区域运算结果替换当前区域成功，false表示区域运算结果替换当前区域失败。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types. |

## quickContains

```TypeScript
quickContains(left: number, top: number, right: number, bottom: number): boolean
```

判断当前区域是否等同于单个矩形并且包含指定矩形。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Region-quickContains(left: int, top: int, right: int, bottom: int): boolean--><!--Device-Region-quickContains(left: int, top: int, right: int, bottom: int): boolean-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| left | number | 是 | 矩形区域的左侧位置。该参数必须为整数。当输入的数字带小数时，小数部分会被舍去。 |
| top | number | 是 | 矩形区域的顶部位置。该参数必须为整数。当输入的数字带小数时，小数部分会被舍去。 |
| right | number | 是 | 矩形区域的右侧位置。该参数必须为整数。当输入的数字带小数时，小数部分会被舍去。 |
| bottom | number | 是 | 矩形区域的底部位置。该参数必须为整数。当输入的数字带小数时，小数部分会被舍去。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回当前区域是否等同于单个矩形并且包含指定矩形的结果。true表示当前区域等同于单个矩形并且包含指定矩形，false表示当前区域不等同于单个矩形或不包含指定矩形。 |

## quickReject

```TypeScript
quickReject(left: number, top: number, right: number, bottom: number): boolean
```

快速判断矩形和区域是否不相交，实际上比较的是矩形和区域的外接矩形是否不相交，因此会有误差。

**起始版本：** 12

<!--Device-Region-quickReject(left: int, top: int, right: int, bottom: int): boolean--><!--Device-Region-quickReject(left: int, top: int, right: int, bottom: int): boolean-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| left | number | 是 | 矩形区域的左侧位置。该参数必须为整数。当输入的数字带小数时，小数部分会被舍去。 |
| top | number | 是 | 矩形区域的顶部位置。该参数必须为整数。当输入的数字带小数时，小数部分会被舍去。 |
| right | number | 是 | 矩形区域的右侧位置。该参数必须为整数。当输入的数字带小数时，小数部分会被舍去。 |
| bottom | number | 是 | 矩形区域的底部位置。该参数必须为整数。当输入的数字带小数时，小数部分会被舍去。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回矩形是否与区域不相交的结果。true表示矩形与区域不相交，false表示矩形与区域相交。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types. |

## quickRejectRegion

```TypeScript
quickRejectRegion(region: Region): boolean
```

判断当前区域是否与另一个区域不相交。实际上比较的是两个区域的外接矩形是否不相交，因此会有误差。

**起始版本：** 20

<!--Device-Region-quickRejectRegion(region: Region): boolean--><!--Device-Region-quickRejectRegion(region: Region): boolean-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| region | [Region](../../apis-image-kit/arkts-apis/arkts-image-image-region-i.md) | 是 | 指定的区域对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回是否当前区域与另外的区域不相交的结果。true表示不相交，false表示相交。仅点和边相交返回true。 |

## setEmpty

```TypeScript
setEmpty(): void
```

设置当前区域为空。

**起始版本：** 20

<!--Device-Region-setEmpty(): void--><!--Device-Region-setEmpty(): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## setPath

```TypeScript
setPath(path: Path, clip: Region): boolean
```

设置一个与裁剪区域内路径轮廓相匹配的区域。

**起始版本：** 12

<!--Device-Region-setPath(path: Path, clip: Region): boolean--><!--Device-Region-setPath(path: Path, clip: Region): boolean-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | [Path](arkts-arkgraphics2d-drawing-path-c.md) | 是 | 路径对象。 |
| clip | [Region](../../apis-image-kit/arkts-apis/arkts-image-image-region-i.md) | 是 | 区域对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回设置一个与裁剪区域内路径轮廓相匹配的区域是否成功。true表示设置成功，false表示设置失败。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types. |

## setRect

```TypeScript
setRect(left: number, top: number, right: number, bottom: number): boolean
```

设置一个矩形区域。

**起始版本：** 12

<!--Device-Region-setRect(left: int, top: int, right: int, bottom: int): boolean--><!--Device-Region-setRect(left: int, top: int, right: int, bottom: int): boolean-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| left | number | 是 | 矩形区域的左侧位置。该参数必须为整数。当输入的数字带小数时，小数部分会被舍去。 |
| top | number | 是 | 矩形区域的顶部位置。该参数必须为整数。当输入的数字带小数时，小数部分会被舍去。 |
| right | number | 是 | 矩形区域的右侧位置。该参数必须为整数。当输入的数字带小数时，小数部分会被舍去。 |
| bottom | number | 是 | 矩形区域的底部位置。该参数必须为整数。当输入的数字带小数时，小数部分会被舍去。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回设置矩形区域是否成功的结果。true表示设置矩形区域成功，false表示设置矩形区域失败。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types. |

## setRegion

```TypeScript
setRegion(region: Region): void
```

设置当前区域为另一块区域。

**起始版本：** 20

<!--Device-Region-setRegion(region: Region): void--><!--Device-Region-setRegion(region: Region): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| region | [Region](../../apis-image-kit/arkts-apis/arkts-image-image-region-i.md) | 是 | 用于赋值的区域。 |

