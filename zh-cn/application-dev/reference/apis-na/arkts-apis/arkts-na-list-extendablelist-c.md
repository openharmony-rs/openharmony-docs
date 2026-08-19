# ExtendableList

定义可扩展List组件。

**继承/实现关系：** ExtendableList implements ListAttribute

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

<!--Device-unnamed-export declare abstract class ExtendableList--><!--Device-unnamed-export declare abstract class ExtendableList-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## $_instantiate

```TypeScript
@ComponentBuilder
  static $_instantiate<T extends ExtendableList>(
    factory: ConstructorT<T>, 
    options?: ListOptions, 
    content_?: CustomBuilder
  ): T
```

可扩展List组件的构造函数。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ExtendableList-@ComponentBuilder  static $_instantiate<T extends ExtendableList>(    factory: ConstructorT<T>,     options?: ListOptions,     content_?: CustomBuilder  ): T--><!--Device-ExtendableList-@ComponentBuilder  static $_instantiate<T extends ExtendableList>(    factory: ConstructorT<T>,     options?: ListOptions,     content_?: CustomBuilder  ): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| factory | [ConstructorT](arkts-na-constructort-t.md)&lt;T&gt; | 是 |  |
| options | [ListOptions](arkts-na-list-listoptions-i.md) | 否 |  |
| content_ | CustomBuilder | 否 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T |  |

## _instantiateImpl

```TypeScript
@Builder
  static _instantiateImpl<T extends ExtendableList>(
    styles: CustomBuilderT<T>, 
    factory: ConstructorT<T>,
    content_?: CustomBuilder
  ): void
```

扩展列表组件入口

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ExtendableList-@Builder  static _instantiateImpl<T extends ExtendableList>(    styles: CustomBuilderT<T>,     factory: ConstructorT<T>,    content_?: CustomBuilder  ): void--><!--Device-ExtendableList-@Builder  static _instantiateImpl<T extends ExtendableList>(    styles: CustomBuilderT<T>,     factory: ConstructorT<T>,    content_?: CustomBuilder  ): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| styles | CustomBuilderT&lt;T&gt; | 是 |  |
| factory | [ConstructorT](arkts-na-constructort-t.md)&lt;T&gt; | 是 |  |
| content_ | CustomBuilder | 否 |  |

## setListOptions

```TypeScript
public setListOptions(options?: ListOptions): this
```

设置List组件参数。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ExtendableList-public setListOptions(options?: ListOptions): this--><!--Device-ExtendableList-public setListOptions(options?: ListOptions): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [ListOptions](arkts-na-list-listoptions-i.md) | 否 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

