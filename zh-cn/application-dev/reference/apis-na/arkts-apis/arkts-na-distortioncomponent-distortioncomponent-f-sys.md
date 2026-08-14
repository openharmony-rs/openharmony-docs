# DistortionComponent（系统接口）

## DistortionComponent

```TypeScript
@ComponentBuilder
export declare function DistortionComponent(
    options?: DistortionComponentOptions,
    content_?:CustomBuilder,
): DistortionComponentAttribute
```

Defines a DistortionComponent that provides spatial distortion visual effects.

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@ComponentBuilderexport declare function DistortionComponent(    options?: DistortionComponentOptions,    content_?:CustomBuilder,): DistortionComponentAttribute--><!--Device-unnamed-@ComponentBuilderexport declare function DistortionComponent(    options?: DistortionComponentOptions,    content_?:CustomBuilder,): DistortionComponentAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [DistortionComponentOptions](arkts-na-distortioncomponent-distortioncomponentoptions-i-sys.md) | 否 | DistortionComponent Options. |
| content_ | CustomBuilder | 否 | Subcomponents of DistortionComponent. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DistortionComponentAttribute](arkts-na-distortioncomponent-distortioncomponentattribute-i.md) |  |

