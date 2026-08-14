# ExtendableText

定义扩展文本组件

**继承/实现关系：** ExtendableText implements TextAttribute

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

<!--Device-unnamed-export declare abstract class ExtendableText--><!--Device-unnamed-export declare abstract class ExtendableText-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## $_instantiate

```TypeScript
@ComponentBuilder
  static $_instantiate<T extends ExtendableText>(
    factory: ConstructorT<T>, 
    content?: string | Resource, 
    value?: TextOptions, 
    content_?: CustomBuilder
  ): T
```

扩展文本组件构造器

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ExtendableText-@ComponentBuilder  static $_instantiate<T extends ExtendableText>(    factory: ConstructorT<T>,     content?: string | Resource,     value?: TextOptions,     content_?: CustomBuilder  ): T--><!--Device-ExtendableText-@ComponentBuilder  static $_instantiate<T extends ExtendableText>(    factory: ConstructorT<T>,     content?: string | Resource,     value?: TextOptions,     content_?: CustomBuilder  ): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| factory | [ConstructorT](../../apis-na/arkts-apis/arkts-na-constructort-t.md)&lt;T&gt; | 是 |  |
| content | string \| [Resource](arkts-arkui-resource-t.md) | 否 |  |
| value | [TextOptions](arkts-arkui-text-textoptions-i.md) | 否 |  |
| content_ | CustomBuilder | 否 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T |  |

## _instantiateImpl

```TypeScript
@Builder
  static _instantiateImpl<T extends ExtendableText>(
      styles: CustomBuilderT<T>, 
      factory: ConstructorT<T>, 
      content_?: CustomBuilder
  ): void
```

扩展文本组件入口

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ExtendableText-@Builder  static _instantiateImpl<T extends ExtendableText>(      styles: CustomBuilderT<T>,       factory: ConstructorT<T>,       content_?: CustomBuilder  ): void--><!--Device-ExtendableText-@Builder  static _instantiateImpl<T extends ExtendableText>(      styles: CustomBuilderT<T>,       factory: ConstructorT<T>,       content_?: CustomBuilder  ): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| styles | CustomBuilderT&lt;T&gt; | 是 |  |
| factory | [ConstructorT](../../apis-na/arkts-apis/arkts-na-constructort-t.md)&lt;T&gt; | 是 |  |
| content_ | CustomBuilder | 否 |  |

## setTextOptions

```TypeScript
public setTextOptions(
    content?: string | Resource, 
    value?: TextOptions
  ): this
```

设置文本组件的选项

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ExtendableText-public setTextOptions(    content?: string | Resource,     value?: TextOptions  ): this--><!--Device-ExtendableText-public setTextOptions(    content?: string | Resource,     value?: TextOptions  ): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| content | string \| [Resource](arkts-arkui-resource-t.md) | 否 |  |
| value | [TextOptions](arkts-arkui-text-textoptions-i.md) | 否 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

