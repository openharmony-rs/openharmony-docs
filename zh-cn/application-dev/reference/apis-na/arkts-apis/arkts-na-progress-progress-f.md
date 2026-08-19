# Progress

## Progress

```TypeScript
@ComponentBuilder
export declare function Progress(
    options: ProgressOptions
): ProgressAttribute
```

创建进度条组件。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@ComponentBuilderexport declare function Progress(    options: ProgressOptions): ProgressAttribute--><!--Device-unnamed-@ComponentBuilderexport declare function Progress(    options: ProgressOptions): ProgressAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [ProgressOptions](arkts-na-progress-progressoptions-i.md) | 是 | 按进度条类型不同，设置不同属性的进度条组件参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ProgressAttribute |  |


## Progress

```TypeScript
@Builder
export declare function Progress(
    style: CustomBuilderT<ProgressAttribute>,
): ProgressAttribute
```

定义Progress组件。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@Builderexport declare function Progress(    style: CustomBuilderT<ProgressAttribute>,): ProgressAttribute--><!--Device-unnamed-@Builderexport declare function Progress(    style: CustomBuilderT<ProgressAttribute>,): ProgressAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | CustomBuilderT&lt;ProgressAttribute&gt; | 是 | Progress属性实例。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ProgressAttribute |  |

