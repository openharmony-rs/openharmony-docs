# LayeredDrawableDescriptor

当传入资源id或name为包含前景和背景资源的json文件时，生成LayeredDrawableDescriptor对象。继承自 [DrawableDescriptor](../../apis-arkui/arkts-apis/arkts-arkui-arkui-drawabledescriptor-drawabledescriptorloadedresult-i.md)。 drawable.json位于项目工程entry/src/main/resources/base/media目录下。定义请参考：

**继承/实现关系：** LayeredDrawableDescriptor extends [DrawableDescriptor](../../apis-arkui/arkts-apis/arkts-arkui-arkui-drawabledescriptor-drawabledescriptor-c.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare class LayeredDrawableDescriptor--><!--Device-unnamed-export declare class LayeredDrawableDescriptor-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## constructor

```TypeScript
constructor(
    foreground?: DrawableDescriptor,
    background?: DrawableDescriptor,
    mask?: DrawableDescriptor
  )
```

LayeredDrawableDescriptor的构造函数。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LayeredDrawableDescriptor-constructor(    foreground?: DrawableDescriptor,    background?: DrawableDescriptor,    mask?: DrawableDescriptor  )--><!--Device-LayeredDrawableDescriptor-constructor(    foreground?: DrawableDescriptor,    background?: DrawableDescriptor,    mask?: DrawableDescriptor  )-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| foreground | [DrawableDescriptor](../../apis-arkui/arkts-apis/arkts-arkui-arkui-drawabledescriptor-drawabledescriptor-c.md) | 否 | 分层图标的前景图片选项。 |
| background | [DrawableDescriptor](../../apis-arkui/arkts-apis/arkts-arkui-arkui-drawabledescriptor-drawabledescriptor-c.md) | 否 | 分层图标的背景图片选项。 |
| mask | [DrawableDescriptor](../../apis-arkui/arkts-apis/arkts-arkui-arkui-drawabledescriptor-drawabledescriptor-c.md) | 否 | 分层图标的遮罩选项。 |

## constructor

```TypeScript
constructor(
```

Creates a new LayeredDrawableDescriptor.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-LayeredDrawableDescriptor-constructor(--><!--Device-LayeredDrawableDescriptor-constructor(-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## getBackground

```TypeScript
getBackground(): DrawableDescriptor | undefined
```

获取背景的DrawableDescriptor对象。 > **说明：** > > DrawableDescriptor对象通过[release](../../apis-arkui/arkts-apis/arkts-arkui-arkui-drawabledescriptor-drawabledescriptor-c.md#release)释放后，本接口返回undefined。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LayeredDrawableDescriptor-getBackground(): DrawableDescriptor | undefined--><!--Device-LayeredDrawableDescriptor-getBackground(): DrawableDescriptor | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DrawableDescriptor](../../apis-arkui/arkts-apis/arkts-arkui-arkui-drawabledescriptor-drawabledescriptor-c.md) | Return the DrawableDescriptor object of background. |

## getForeground

```TypeScript
getForeground(): DrawableDescriptor | undefined
```

获取前景的DrawableDescriptor对象。 > **说明：** > > DrawableDescriptor对象通过[release](../../apis-arkui/arkts-apis/arkts-arkui-arkui-drawabledescriptor-drawabledescriptor-c.md#release)释放后，本接口返回undefined。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LayeredDrawableDescriptor-getForeground(): DrawableDescriptor | undefined--><!--Device-LayeredDrawableDescriptor-getForeground(): DrawableDescriptor | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DrawableDescriptor](../../apis-arkui/arkts-apis/arkts-arkui-arkui-drawabledescriptor-drawabledescriptor-c.md) | Return the DrawableDescriptor object of foreground. |

## getMask

```TypeScript
getMask(): DrawableDescriptor | undefined
```

获取蒙版的DrawableDescriptor对象。 > **说明：** > > DrawableDescriptor对象通过[release](../../apis-arkui/arkts-apis/arkts-arkui-arkui-drawabledescriptor-drawabledescriptor-c.md#release)释放后，本接口返回undefined。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LayeredDrawableDescriptor-getMask(): DrawableDescriptor | undefined--><!--Device-LayeredDrawableDescriptor-getMask(): DrawableDescriptor | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DrawableDescriptor](../../apis-arkui/arkts-apis/arkts-arkui-arkui-drawabledescriptor-drawabledescriptor-c.md) | Return the DrawableDescriptor object of mask. |

## getMaskClipPath

```TypeScript
static getMaskClipPath(): string
```

LayeredDrawableDescriptor的静态方法，获取系统内置的裁切路径参数。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LayeredDrawableDescriptor-static getMaskClipPath(): string--><!--Device-LayeredDrawableDescriptor-static getMaskClipPath(): string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回裁切路径的命令字符串。 |

## setBlendMode

```TypeScript
setBlendMode(mode: drawing.BlendMode | undefined): void
```

设置LayeredDrawableDescriptor的混合模式。对同一LayeredDrawableDescriptor对象多次调用setBlendMode接口时， 仅在绘制完成前的最后一次调用生效。该接口不支持动态切换。 LayeredDrawableDescriptor的默认绘制顺序为背景、蒙版、前景。设置了混合模式后，绘制顺序变为背景、前景、蒙版。 若设置的值无效，会按照未设置混合模式进行绘制。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LayeredDrawableDescriptor-setBlendMode(mode: drawing.BlendMode | undefined): void--><!--Device-LayeredDrawableDescriptor-setBlendMode(mode: drawing.BlendMode | undefined): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | drawing.BlendMode \| undefined | 是 | 混合模式。设置undefined，会按照未设置混合模式进行绘制。 |

