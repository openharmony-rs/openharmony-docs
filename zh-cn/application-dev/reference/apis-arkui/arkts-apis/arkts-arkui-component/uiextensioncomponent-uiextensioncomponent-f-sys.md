# UIExtensionComponent（系统接口）

## UIExtensionComponent

```TypeScript
export declare function UIExtensionComponent(
    want: Want, options?: UIExtensionOptions
): UIExtensionComponentAttribute
```

定义UIExtensionComponent组件。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export declare function UIExtensionComponent(    want: Want, options?: UIExtensionOptions): UIExtensionComponentAttribute--><!--Device-unnamed-export declare function UIExtensionComponent(    want: Want, options?: UIExtensionOptions): UIExtensionComponentAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 要加载的Ability，必须是带UI的Ability扩展。Want的parameters中需设置ability.want.params.uiExtensionType字段，取值需与扩展Ability在module.json5中配置的type一致。 |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 需要传递的构造参数，用于自定义UIExtensionComponent的配置（如设置占位符、DPI跟随策略、窗口Mode跟随策略等）。当需要自定义上述配置时传入此参数，不传入时使用默认配置。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ |  |


## UIExtensionComponent

```TypeScript
export declare function UIExtensionComponent(
    style: CustomBuilderT<UIExtensionComponentAttribute>
): UIExtensionComponentAttribute
```

定义UIExtensionComponent组件。它要求在组件属性设置开始时调用setUIExtensionComponentOptions， 并在组件属性设置结束时调用applyAttributeFinish。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**装饰器类型：** @Builder

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export declare function UIExtensionComponent(    style: CustomBuilderT<UIExtensionComponentAttribute>): UIExtensionComponentAttribute--><!--Device-unnamed-export declare function UIExtensionComponent(    style: CustomBuilderT<UIExtensionComponentAttribute>): UIExtensionComponentAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;\_\_\_MD\_LINK\_USD\_1\_\_\_&gt; | 是 | 用于设置uiextensioncomponent属性的回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | UIExtensionComponent的属性。 |

