# ContainerSpan

## ContainerSpan

```TypeScript
@ComponentBuilder
export declare function ContainerSpan(
    content_?: CustomBuilder,
): ContainerSpanAttribute
```

定义ContainerSpan组件。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@ComponentBuilderexport declare function ContainerSpan(    content_?: CustomBuilder,): ContainerSpanAttribute--><!--Device-unnamed-@ComponentBuilderexport declare function ContainerSpan(    content_?: CustomBuilder,): ContainerSpanAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| content_ | CustomBuilder | 否 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ContainerSpanAttribute |  |


## ContainerSpan

```TypeScript
@Builder
export declare function ContainerSpan(
    style: CustomBuilderT<ContainerSpanAttribute>,
    content_?: CustomBuilder,
): ContainerSpanAttribute
```

定义ContainerSpan组件。

**起始版本：** 26.1.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.1.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@Builderexport declare function ContainerSpan(    style: CustomBuilderT<ContainerSpanAttribute>,    content_?: CustomBuilder,): ContainerSpanAttribute--><!--Device-unnamed-@Builderexport declare function ContainerSpan(    style: CustomBuilderT<ContainerSpanAttribute>,    content_?: CustomBuilder,): ContainerSpanAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | CustomBuilderT&lt;ContainerSpanAttribute&gt; | 是 | containerspan属性实例。 |
| content_ | CustomBuilder | 否 | 容器。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ContainerSpanAttribute |  |

