# ContainerReader

## 导入模块

```TypeScript
```

## ContainerReader

```TypeScript
@ComponentBuilder
export declare function ContainerReader(
    value: ContainerReaderInfo,
    content_?: CustomBuilder,
): ContainerReaderAttribute
```

创建容器断点组件并配置容器读取参数。可以包含子组件。 ContainerReader是容器断点组件，用于在动态场景下根据容器尺寸获取断点信息并进行响应式布局。该组件通过 [双向绑定](../../../ui/state-management/arkts-new-binding.md#系统组件参数双向绑定) 实时返回容器的尺寸和断点，使开发者能够基于容器大小进行差异化的组件创建和布局。 > **说明：** > > - 使用ContainerReader时，ContainerReader父组件不要依赖其子组件确定自身尺寸。 > - 容器断点基于组件自身的实际尺寸和断点阈值数组确定高度和宽度断点值，组件尺寸和断点信息仅作用于当前组件及其子组件，同一页面中的多个容器可拥有各自独立的断点状态。 > - ContainerReader组件的尺寸需要由父容器和自身布局确定，不受子组件影响。在不同父容器下的布局规格：父容器为 > [Flex](../../../reference/apis-arkui/arkui-ts/ts-container-flex.md)、 > [Column](../../../reference/apis-arkui/arkui-ts/ts-container-column.md)、 > [Row](../../../reference/apis-arkui/arkui-ts/ts-container-row.md) > 时撑满容器剩余空间；父容器为其他类型时撑满父容器。 > - ContainerReader接口的参数必须使用状态变量结合双向绑定形式([!!语法](../../../ui/state-management/arkts-new-binding.md))， > 以便在后端计算尺寸变化时及时通知前端刷新UI。 > - 更多关于容器断点的开发指导和完整示例，可参考[容器断点 (ContainerReader)](../../../ui/arkts-layout-development-container-reader.md)。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@ComponentBuilderexport declare function ContainerReader(    value: ContainerReaderInfo,    content_?: CustomBuilder,): ContainerReaderAttribute--><!--Device-unnamed-@ComponentBuilderexport declare function ContainerReader(    value: ContainerReaderInfo,    content_?: CustomBuilder,): ContainerReaderAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ContainerReaderInfo](../../apis-arkui/arkts-apis/arkts-arkui-arkui-components-containerreader-containerreaderinfo-i.md) | 是 | 容器读取配置选项，包含尺寸数据和断点配置。 |
| content_ | CustomBuilder | 否 | container |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ContainerReaderAttribute](../../apis-arkui/arkts-apis/arkts-arkui-arkui-components-containerreader-containerreaderattribute-c.md) |  |


## ContainerReader

```TypeScript
@Builder
export declare function ContainerReader(
    style_: CustomBuilderT<ContainerReaderInfo>,
    content_?: CustomBuilder
): ContainerReaderAttribute
```

Defines ContainerReader Component.

**起始版本：** 26.1.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.1.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@Builderexport declare function ContainerReader(    style_: CustomBuilderT<ContainerReaderInfo>,    content_?: CustomBuilder): ContainerReaderAttribute--><!--Device-unnamed-@Builderexport declare function ContainerReader(    style_: CustomBuilderT<ContainerReaderInfo>,    content_?: CustomBuilder): ContainerReaderAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style_ | CustomBuilderT&lt;[ContainerReaderInfo](../../apis-arkui/arkts-apis/arkts-arkui-arkui-components-containerreader-containerreaderinfo-i.md)&gt; | 是 | The custom builder function for container content. |
| content_ | CustomBuilder | 否 | The configuration options for containerreader. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ContainerReaderAttribute](../../apis-arkui/arkts-apis/arkts-arkui-arkui-components-containerreader-containerreaderattribute-c.md) | The attribute of the containerreader |

