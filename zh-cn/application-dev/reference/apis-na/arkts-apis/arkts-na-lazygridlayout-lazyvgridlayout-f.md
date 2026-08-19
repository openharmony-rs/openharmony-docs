# LazyVGridLayout

## LazyVGridLayout

```TypeScript
@ComponentBuilder
export declare function LazyVGridLayout(
    content_?: CustomBuilder,
): LazyVGridLayoutAttribute
```

创建垂直方向懒加载网格布局容器。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@ComponentBuilderexport declare function LazyVGridLayout(    content_?: CustomBuilder,): LazyVGridLayoutAttribute--><!--Device-unnamed-@ComponentBuilderexport declare function LazyVGridLayout(    content_?: CustomBuilder,): LazyVGridLayoutAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| content_ | CustomBuilder | 否 | 容器内容。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| LazyVGridLayoutAttribute | 返回LazyVGridLayout组件的属性。 |


## LazyVGridLayout

```TypeScript
@Builder
export declare function LazyVGridLayout(
    style_: CustomBuilderT<LazyVGridLayoutAttribute>,
    content_?: CustomBuilder
): LazyVGridLayoutAttribute
```

定义LazyVGridLayout组件。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@Builderexport declare function LazyVGridLayout(    style_: CustomBuilderT<LazyVGridLayoutAttribute>,    content_?: CustomBuilder): LazyVGridLayoutAttribute--><!--Device-unnamed-@Builderexport declare function LazyVGridLayout(    style_: CustomBuilderT<LazyVGridLayoutAttribute>,    content_?: CustomBuilder): LazyVGridLayoutAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style_ | CustomBuilderT&lt;LazyVGridLayoutAttribute&gt; | 是 | 创建LazyVGridLayout的样式 |
| content_ | CustomBuilder | 否 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| LazyVGridLayoutAttribute | LazyVGridLayout的属性。 |

