# MaskFilter

蒙版滤镜对象，用于对绘制内容施加模糊效果。 > **说明：** > > - 本Class首批接口从API version 12开始支持。 > > - 本模块使用屏幕物理像素单位px。 > > - 本模块为单线程模型策略，需要调用方自行管理线程安全和上下文状态的切换。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-drawing-class MaskFilter--><!--Device-drawing-class MaskFilter-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## createBlurMaskFilter

```TypeScript
static createBlurMaskFilter(blurType: BlurType, sigma: number): MaskFilter
```

创建具有模糊效果的蒙版滤镜。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

<!--Device-MaskFilter-static createBlurMaskFilter(blurType: BlurType, sigma: number): MaskFilter--><!--Device-MaskFilter-static createBlurMaskFilter(blurType: BlurType, sigma: number): MaskFilter-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| blurType | [BlurType](arkts-arkgraphics2d-drawing-blurtype-e.md) | 是 | 模糊类型，用于指定蒙版滤镜的模糊操作方式。 |
| sigma | number | 是 | 高斯模糊的标准偏差，必须为大于0的浮点数。单位为物理像素px。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [MaskFilter](arkts-arkgraphics2d-drawing-maskfilter-c.md) | 返回创建的蒙版滤镜对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; &lt;br&gt;2. Incorrect parameter types; 3. Parameter verification failed. |

## createBlurMaskFilter

```TypeScript
static createBlurMaskFilter(blurType: BlurType, sigma: double): MaskFilter | undefined
```

创建具有模糊效果的蒙版滤镜。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-MaskFilter-static createBlurMaskFilter(blurType: BlurType, sigma: double): MaskFilter | undefined--><!--Device-MaskFilter-static createBlurMaskFilter(blurType: BlurType, sigma: double): MaskFilter | undefined-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| blurType | [BlurType](arkts-arkgraphics2d-drawing-blurtype-e.md) | 是 | 模糊类型，用于指定蒙版滤镜的模糊操作方式。 |
| sigma | double | 是 | 高斯模糊的标准偏差，必须为大于0的浮点数。单位为物理像素px。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [MaskFilter](arkts-arkgraphics2d-drawing-maskfilter-c.md) | 返回创建的蒙版滤镜对象。创建失败时返回undefined。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; &lt;br&gt;2. Incorrect parameter types; 3. Parameter verification failed. |

