# ExtendableText

定义扩展文本组件

**继承/实现关系：** ExtendableText implements [TextAttribute](text-textattribute-i.md)

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

<!--Device-unnamed-export declare abstract class ExtendableText implements TextAttribute--><!--Device-unnamed-export declare abstract class ExtendableText implements TextAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## $_instantiate

```TypeScript
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

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ExtendableText-static $_instantiate<T extends ExtendableText>(    factory: ConstructorT<T>,     content?: string | Resource,     value?: TextOptions,     content_?: CustomBuilder  ): T--><!--Device-ExtendableText-static $_instantiate<T extends ExtendableText>(    factory: ConstructorT<T>,     content?: string | Resource,     value?: TextOptions,     content_?: CustomBuilder  ): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| factory | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;T&gt; | 是 |  |
| content | string \| Resource | 否 |  |
| value | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 |  |
| content\_ | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T |  |

## _instantiateImpl

```TypeScript
static _instantiateImpl<T extends ExtendableText>(
      styles: CustomBuilderT<T>, 
      factory: ConstructorT<T>, 
      content_?: CustomBuilder
  ): void
```

扩展文本组件入口

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**装饰器类型：** @Builder

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ExtendableText-static _instantiateImpl<T extends ExtendableText>(      styles: CustomBuilderT<T>,       factory: ConstructorT<T>,       content_?: CustomBuilder  ): void--><!--Device-ExtendableText-static _instantiateImpl<T extends ExtendableText>(      styles: CustomBuilderT<T>,       factory: ConstructorT<T>,       content_?: CustomBuilder  ): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| styles | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;T&gt; | 是 |  |
| factory | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;T&gt; | 是 |  |
| content\_ | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 |  |

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

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ExtendableText-public setTextOptions(    content?: string | Resource,     value?: TextOptions  ): this--><!--Device-ExtendableText-public setTextOptions(    content?: string | Resource,     value?: TextOptions  ): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| content | string \| Resource | 否 |  |
| value | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

