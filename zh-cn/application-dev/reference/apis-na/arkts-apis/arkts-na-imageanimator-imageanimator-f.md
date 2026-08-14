# ImageAnimator

## ImageAnimator

```TypeScript
@ComponentBuilder
export declare function ImageAnimator(): ImageAnimatorAttribute
```

Defines the ImageAnimator component.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@ComponentBuilderexport declare function ImageAnimator(): ImageAnimatorAttribute--><!--Device-unnamed-@ComponentBuilderexport declare function ImageAnimator(): ImageAnimatorAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ImageAnimatorAttribute | The attribute of the ImageAnimator. |


## ImageAnimator

```TypeScript
@Builder
export declare function ImageAnimator(style: CustomBuilderT<ImageAnimatorAttribute>): ImageAnimatorAttribute
```

定义ImageAnimator组件。它需要在组件开始时调用setImageAnimatorOptions 属性设置。并且它需要在组件属性设置结束时调用applyAttributeFinish。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@Builderexport declare function ImageAnimator(style: CustomBuilderT<ImageAnimatorAttribute>): ImageAnimatorAttribute--><!--Device-unnamed-@Builderexport declare function ImageAnimator(style: CustomBuilderT<ImageAnimatorAttribute>): ImageAnimatorAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | CustomBuilderT&lt;ImageAnimatorAttribute&gt; | 是 | 设置组件属性的回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ImageAnimatorAttribute | ImageAnimator的属性。 |

