# Badge

## Badge

```TypeScript
@ComponentBuilder
export declare function Badge(
    value: BadgeParamWithNumber | BadgeParamWithString, 
    content_?: CustomBuilder
): BadgeAttribute
```

根据数字或者字符串创建标记组件。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@ComponentBuilderexport declare function Badge(    value: BadgeParamWithNumber | BadgeParamWithString,     content_?: CustomBuilder): BadgeAttribute--><!--Device-unnamed-@ComponentBuilderexport declare function Badge(    value: BadgeParamWithNumber | BadgeParamWithString,     content_?: CustomBuilder): BadgeAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [BadgeParamWithNumber](arkts-na-badge-badgeparamwithnumber-i.md) \| [BadgeParamWithString](arkts-na-badge-badgeparamwithstring-i.md) | 是 | 数字、字符串类型的标记组件参数。 |
| content_ | CustomBuilder | 否 | 子组件。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| BadgeAttribute |  |


## Badge

```TypeScript
@Builder
export declare function Badge(
    style: CustomBuilderT<BadgeAttribute>,
    content_?: CustomBuilder,
): BadgeAttribute
```

定义Badge组件

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@Builderexport declare function Badge(    style: CustomBuilderT<BadgeAttribute>,    content_?: CustomBuilder,): BadgeAttribute--><!--Device-unnamed-@Builderexport declare function Badge(    style: CustomBuilderT<BadgeAttribute>,    content_?: CustomBuilder,): BadgeAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | CustomBuilderT&lt;BadgeAttribute&gt; | 是 | badge属性实例。 |
| content_ | CustomBuilder | 否 | 子组件。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| BadgeAttribute |  |

