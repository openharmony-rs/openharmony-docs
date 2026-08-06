# EmbeddedComponent

## EmbeddedComponent

```TypeScript
export declare function EmbeddedComponent(
    loader: Want, type?: EmbeddedType
): EmbeddedComponentAttribute
```

创建跨进程嵌入式组件，用于显示同包名或满足跨应用权限条件的EmbeddedUIExtensionAbility的UI。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export declare function EmbeddedComponent(    loader: Want, type?: EmbeddedType): EmbeddedComponentAttribute--><!--Device-unnamed-export declare function EmbeddedComponent(    loader: Want, type?: EmbeddedType): EmbeddedComponentAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| loader | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 要加载的EmbeddedUIExtensionAbility。 |
| type | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 提供方的类型，当前支持值为EmbeddedType.EMBEDDED\_\_\_ESCAPED\_UNDERSCORE\_\_\_UI\_\_\_ESCAPED\_UNDERSCORE\_\_\_EXTENSION，表示嵌入的是EmbeddedUIExtensionAbility提供的UI。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ |  |


## EmbeddedComponent

```TypeScript
export declare function EmbeddedComponent(
    loader: Want, type?: EmbeddedType, options?: EmbeddedOptions
): EmbeddedComponentAttribute
```

创建跨进程嵌入式组件，用于显示同包名或满足跨应用权限条件的EmbeddedUIExtensionAbility的UI。相对于API version 12的接口，新增options参数用于传递构造参数。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export declare function EmbeddedComponent(    loader: Want, type?: EmbeddedType, options?: EmbeddedOptions): EmbeddedComponentAttribute--><!--Device-unnamed-export declare function EmbeddedComponent(    loader: Want, type?: EmbeddedType, options?: EmbeddedOptions): EmbeddedComponentAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| loader | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 要加载的EmbeddedUIExtensionAbility。 |
| type | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 提供方的类型，当前支持值为EmbeddedType.EMBEDDED\_\_\_ESCAPED\_UNDERSCORE\_\_\_UI\_\_\_ESCAPED\_UNDERSCORE\_\_\_EXTENSION，表示嵌入的是EmbeddedUIExtensionAbility提供的UI。 |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 嵌入式组件的可选配置项，用于设置占位符、DPI跟随策略、窗口模式跟随策略等。详见EmbeddedOptions。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ |  |


## EmbeddedComponent

```TypeScript
export declare function EmbeddedComponent(
    style: CustomBuilderT<EmbeddedComponentAttribute>
): EmbeddedComponentAttribute
```

定义EmbeddedComponent组件。需要在组件属性设置开始时调用setEmbeddedComponentOptions， 并在组件属性设置结束时调用applyAttributeFinish。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**装饰器类型：** @Builder

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export declare function EmbeddedComponent(    style: CustomBuilderT<EmbeddedComponentAttribute>): EmbeddedComponentAttribute--><!--Device-unnamed-export declare function EmbeddedComponent(    style: CustomBuilderT<EmbeddedComponentAttribute>): EmbeddedComponentAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;\_\_\_MD\_LINK\_USD\_1\_\_\_&gt; | 是 | 用于设置embeddedcomponent属性的回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | EmbeddedComponent的属性。 |

