# WaterFlow

## WaterFlow

```TypeScript
@ComponentBuilder
export declare function WaterFlow(
    options?: WaterFlowOptions, 
    content_?: CustomBuilder,
): WaterFlowAttribute
```

定义瀑布流组件。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@ComponentBuilderexport declare function WaterFlow(    options?: WaterFlowOptions,     content_?: CustomBuilder,): WaterFlowAttribute--><!--Device-unnamed-@ComponentBuilderexport declare function WaterFlow(    options?: WaterFlowOptions,     content_?: CustomBuilder,): WaterFlowAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [WaterFlowOptions](arkts-na-waterflow-waterflowoptions-i.md) | 否 |  |
| content_ | CustomBuilder | 否 | 子组件 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| WaterFlowAttribute |  |


## WaterFlow

```TypeScript
@Builder
export declare function WaterFlow(
    style_: CustomBuilderT<WaterFlowAttribute>, 
    content_?: CustomBuilder
): WaterFlowAttribute
```

定义WaterFlow组件。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@Builderexport declare function WaterFlow(    style_: CustomBuilderT<WaterFlowAttribute>,     content_?: CustomBuilder): WaterFlowAttribute--><!--Device-unnamed-@Builderexport declare function WaterFlow(    style_: CustomBuilderT<WaterFlowAttribute>,     content_?: CustomBuilder): WaterFlowAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style_ | CustomBuilderT&lt;WaterFlowAttribute&gt; | 是 | 创建WaterFlow的样式 |
| content_ | CustomBuilder | 否 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| WaterFlowAttribute | WaterFlow的属性。 |

