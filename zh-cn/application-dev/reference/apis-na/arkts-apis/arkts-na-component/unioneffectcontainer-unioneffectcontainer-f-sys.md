# UnionEffectContainer（系统接口）

## UnionEffectContainer

```TypeScript
export declare function UnionEffectContainer(
    options?:UnionEffectContainerOptions,
    content_?:CustomBuilder,
): UnionEffectContainerAttribute
```

Provides a UnionEffectContainer Component that generates a component fusion effect for descendant components with "useUnionEffect(true)" set inside it, when their distance is less than a certain threshold.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export declare function UnionEffectContainer(    options?:UnionEffectContainerOptions,    content_?:CustomBuilder,): UnionEffectContainerAttribute--><!--Device-unnamed-export declare function UnionEffectContainer(    options?:UnionEffectContainerOptions,    content_?:CustomBuilder,): UnionEffectContainerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | The options to create a UnionEffectContainer. |
| content\_ | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | Subcomponents of UnionEffectContainer |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ |  |


## UnionEffectContainer

```TypeScript
export declare function UnionEffectContainer(
  style_: CustomBuilderT<UnionEffectContainerAttribute>,
  content_?: CustomBuilder,
): UnionEffectContainerAttribute
```

Defines UnionEffectContainer

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**装饰器类型：** @Builder

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export declare function UnionEffectContainer(  style_: CustomBuilderT<UnionEffectContainerAttribute>,  content_?: CustomBuilder,): UnionEffectContainerAttribute--><!--Device-unnamed-export declare function UnionEffectContainer(  style_: CustomBuilderT<UnionEffectContainerAttribute>,  content_?: CustomBuilder,): UnionEffectContainerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style\_ | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;\_\_\_MD\_LINK\_USD\_1\_\_\_&gt; | 是 | UnionEffectContainer attribute instance |
| content\_ | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | container |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ |  |

