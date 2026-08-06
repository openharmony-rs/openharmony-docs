# ArcList

## ArcList

```TypeScript
export declare function ArcList(
    options?: ArkListOptions, 
    content_?: CustomBuilder,
): ArcListAttribute
```

创建弧形列表实例，传入弧形列表配置项参数。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare function ArcList(    options?: ArkListOptions,     content_?: CustomBuilder,): ArcListAttribute--><!--Device-unnamed-export declare function ArcList(    options?: ArkListOptions,     content_?: CustomBuilder,): ArcListAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 |  |
| content\_ | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ |  |


## ArcList

```TypeScript
export declare function ArcList(
    style_: CustomBuilderT<ArcListAttribute>,
    content_?: CustomBuilder
): ArcListAttribute
```

定义ArcList组件。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**装饰器类型：** @Builder

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export declare function ArcList(    style_: CustomBuilderT<ArcListAttribute>,    content_?: CustomBuilder): ArcListAttribute--><!--Device-unnamed-export declare function ArcList(    style_: CustomBuilderT<ArcListAttribute>,    content_?: CustomBuilder): ArcListAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style\_ | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;ArcListAttribute&gt; | 是 | The style to create an ArcList. |
| content\_ | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | ArcList的属性。 |

