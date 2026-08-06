# SecurityUIExtensionComponent（系统接口）

## SecurityUIExtensionComponent

```TypeScript
export declare function SecurityUIExtensionComponent(
    want: Want, options?: SecurityUIExtensionOptions, 
    content_?: CustomBuilder,
): SecurityUIExtensionComponentAttribute
```

创建SecurityUIExtensionComponent组件，用于嵌入显示远程UIExtensionAbility提供的UI。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export declare function SecurityUIExtensionComponent(    want: Want, options?: SecurityUIExtensionOptions,     content_?: CustomBuilder,): SecurityUIExtensionComponentAttribute--><!--Device-unnamed-export declare function SecurityUIExtensionComponent(    want: Want, options?: SecurityUIExtensionOptions,     content_?: CustomBuilder,): SecurityUIExtensionComponentAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 要加载的Ability信息。通过bundleName和abilityName共同确定被拉起的UIExtensionAbility，同时需要在parameters中配置ability.want.params.uiExtensionType字段指定UIExtensionAbility的类型，当前仅支持'sysPicker/photoPicker'。 |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 用于构造SecurityUIExtensionComponent的参数。不填时各字段使用默认值。 |
| content\_ | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 容器内容构建器。ArkTS-Sta模式下可传入自定义内容构建器。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ |  |


## SecurityUIExtensionComponent

```TypeScript
export declare function SecurityUIExtensionComponent(
    style: CustomBuilderT<SecurityUIExtensionComponentAttribute>,
    content_?: CustomBuilder,
): SecurityUIExtensionComponentAttribute
```

定义SecurityUIExtensionComponent组件。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**装饰器类型：** @Builder

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export declare function SecurityUIExtensionComponent(    style: CustomBuilderT<SecurityUIExtensionComponentAttribute>,    content_?: CustomBuilder,): SecurityUIExtensionComponentAttribute--><!--Device-unnamed-export declare function SecurityUIExtensionComponent(    style: CustomBuilderT<SecurityUIExtensionComponentAttribute>,    content_?: CustomBuilder,): SecurityUIExtensionComponentAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;\_\_\_MD\_LINK\_USD\_1\_\_\_&gt; | 是 | 用于设置SecurityUIExtensionComponent属性的回调。 |
| content\_ | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 容器 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | SecurityUIExtensionComponent的属性。 |

