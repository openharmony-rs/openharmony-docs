# ExtendableGridItem

可扩展的GridItem组件。

**继承/实现关系：** ExtendableGridItem implements GridItemAttribute

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

<!--Device-unnamed-export declare abstract class ExtendableGridItem--><!--Device-unnamed-export declare abstract class ExtendableGridItem-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## $_instantiate

```TypeScript
@ComponentBuilder
  static $_instantiate<T extends ExtendableGridItem>(
    factory: ConstructorT<T>, 
    value?: GridItemOptions, 
    content_?: CustomBuilder
  ): T
```

可扩展的GridItem组件的构造函数。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ExtendableGridItem-@ComponentBuilder  static $_instantiate<T extends ExtendableGridItem>(    factory: ConstructorT<T>,     value?: GridItemOptions,     content_?: CustomBuilder  ): T--><!--Device-ExtendableGridItem-@ComponentBuilder  static $_instantiate<T extends ExtendableGridItem>(    factory: ConstructorT<T>,     value?: GridItemOptions,     content_?: CustomBuilder  ): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| factory | [ConstructorT](arkts-na-constructort-t.md)&lt;T&gt; | 是 |  |
| value | [GridItemOptions](arkts-na-griditem-griditemoptions-i.md) | 否 |  |
| content_ | CustomBuilder | 否 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T |  |

## _instantiateImpl

```TypeScript
@Builder
  static _instantiateImpl<T extends ExtendableGridItem>(
    styles: CustomBuilderT<T>, 
    factory: ConstructorT<T>, 
    content_?: CustomBuilder
  ): void
```

扩展网格项组件入口

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ExtendableGridItem-@Builder  static _instantiateImpl<T extends ExtendableGridItem>(    styles: CustomBuilderT<T>,     factory: ConstructorT<T>,     content_?: CustomBuilder  ): void--><!--Device-ExtendableGridItem-@Builder  static _instantiateImpl<T extends ExtendableGridItem>(    styles: CustomBuilderT<T>,     factory: ConstructorT<T>,     content_?: CustomBuilder  ): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| styles | CustomBuilderT&lt;T&gt; | 是 |  |
| factory | [ConstructorT](arkts-na-constructort-t.md)&lt;T&gt; | 是 |  |
| content_ | CustomBuilder | 否 |  |

## setGridItemOptions

```TypeScript
public setGridItemOptions(value?: GridItemOptions): this
```

设置GridItem组件参数。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ExtendableGridItem-public setGridItemOptions(value?: GridItemOptions): this--><!--Device-ExtendableGridItem-public setGridItemOptions(value?: GridItemOptions): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [GridItemOptions](arkts-na-griditem-griditemoptions-i.md) | 否 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

