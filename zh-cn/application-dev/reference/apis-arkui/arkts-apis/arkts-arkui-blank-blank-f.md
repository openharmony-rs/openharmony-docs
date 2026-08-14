# Blank

## Blank

```TypeScript
@ComponentBuilder
export declare function Blank(
    min?: double | string,
): BlankAttribute
```

空白填充组件，在容器主轴方向上，空白填充组件具有自动填充容器空余部分的能力。 仅当父组件为[Row](../../../reference/apis-arkui/arkui-ts/ts-container-row.md)/ [Column](../../../reference/apis-arkui/arkui-ts/ts-container-column.md)/ [Flex](../../../reference/apis-arkui/arkui-ts/ts-container-flex.md)时生效。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@ComponentBuilderexport declare function Blank(    min?: double | string,): BlankAttribute--><!--Device-unnamed-@ComponentBuilderexport declare function Blank(    min?: double | string,): BlankAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| min | double \| string | 否 | 空白填充组件在容器主轴上的最小大小。&lt;br&gt; 默认值：0，number类型单位为vp，string类型可以显式指定 [像素单位](../../../reference/apis-arkui/arkui-ts/ts-pixel-units.md)， 如'10px'。不指定像素单位时，默认单位vp，如'10'，等同于10vp。&lt;br&gt; 非法值：按默认值处理。&lt;br&gt; **说明：**&lt;br&gt; 不支持设置百分比。负值使用默认值。当最小值大于容器可用空间时， 使用最小值作为自身大小并超出容器。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| BlankAttribute |  |


## Blank

```TypeScript
@Builder
export declare function Blank(
    style: CustomBuilderT<BlankAttribute>
): BlankAttribute
```

Defines Blank Component.

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@Builderexport declare function Blank(    style: CustomBuilderT<BlankAttribute>): BlankAttribute--><!--Device-unnamed-@Builderexport declare function Blank(    style: CustomBuilderT<BlankAttribute>): BlankAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | CustomBuilderT&lt;BlankAttribute&gt; | 是 | Blank options. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| BlankAttribute |  |

