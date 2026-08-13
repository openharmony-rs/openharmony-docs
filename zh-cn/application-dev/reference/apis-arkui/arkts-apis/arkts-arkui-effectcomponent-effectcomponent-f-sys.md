# EffectComponent（系统接口）

## EffectComponent

```TypeScript
@ComponentBuilder
export declare function EffectComponent(
    options?: EffectComponentOptions,
    content_?: CustomBuilder,
): EffectComponentAttribute
```

Defines EffectComponent Component

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@ComponentBuilderexport declare function EffectComponent(    options?: EffectComponentOptions,    content_?: CustomBuilder,): EffectComponentAttribute--><!--Device-unnamed-@ComponentBuilderexport declare function EffectComponent(    options?: EffectComponentOptions,    content_?: CustomBuilder,): EffectComponentAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [EffectComponentOptions](arkts-arkui-effectcomponent-effectcomponentoptions-i-sys.md) | 否 | The options to create an EffectComponent. |
| content_ | CustomBuilder | 否 | Subcomponents of EffectComponent |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| EffectComponentAttribute |  |


## EffectComponent

```TypeScript
@Builder
export declare function EffectComponent(
    style_: CustomBuilderT<EffectComponentAttribute>,
    content_?: CustomBuilder,
): EffectComponentAttribute
```

Defines EffectComponent

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@Builderexport declare function EffectComponent(    style_: CustomBuilderT<EffectComponentAttribute>,    content_?: CustomBuilder,): EffectComponentAttribute--><!--Device-unnamed-@Builderexport declare function EffectComponent(    style_: CustomBuilderT<EffectComponentAttribute>,    content_?: CustomBuilder,): EffectComponentAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style_ | CustomBuilderT&lt;EffectComponentAttribute&gt; | 是 | EffectComponent attribute instance |
| content_ | CustomBuilder | 否 | container |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| EffectComponentAttribute |  |

