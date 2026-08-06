# ExtendableList

定义可扩展List组件。

**继承/实现关系：** ExtendableList implements [ListAttribute](list-listattribute-i.md)

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

<!--Device-unnamed-export declare abstract class ExtendableList implements ListAttribute--><!--Device-unnamed-export declare abstract class ExtendableList implements ListAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## $_instantiate

```TypeScript
static $_instantiate<T extends ExtendableList>(
    factory: ConstructorT<T>, 
    options?: ListOptions, 
    content_?: CustomBuilder
  ): T
```

可扩展List组件的构造函数。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ExtendableList-static $_instantiate<T extends ExtendableList>(    factory: ConstructorT<T>,     options?: ListOptions,     content_?: CustomBuilder  ): T--><!--Device-ExtendableList-static $_instantiate<T extends ExtendableList>(    factory: ConstructorT<T>,     options?: ListOptions,     content_?: CustomBuilder  ): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| factory | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;T&gt; | 是 |  |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 |  |
| content\_ | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T |  |

## _instantiateImpl

```TypeScript
static _instantiateImpl<T extends ExtendableList>(
    styles: CustomBuilderT<T>, 
    factory: ConstructorT<T>,
    content_?: CustomBuilder
  ): void
```

扩展列表组件入口

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**装饰器类型：** @Builder

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ExtendableList-static _instantiateImpl<T extends ExtendableList>(    styles: CustomBuilderT<T>,     factory: ConstructorT<T>,    content_?: CustomBuilder  ): void--><!--Device-ExtendableList-static _instantiateImpl<T extends ExtendableList>(    styles: CustomBuilderT<T>,     factory: ConstructorT<T>,    content_?: CustomBuilder  ): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| styles | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;T&gt; | 是 |  |
| factory | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;T&gt; | 是 |  |
| content\_ | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 |  |

## setListOptions

```TypeScript
public setListOptions(options?: ListOptions): this
```

设置List组件参数。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ExtendableList-public setListOptions(options?: ListOptions): this--><!--Device-ExtendableList-public setListOptions(options?: ListOptions): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

