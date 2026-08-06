# Scroll

## Scroll

```TypeScript
export declare function Scroll(
    scroller?: Scroller, 
    content_?: CustomBuilder,
): ScrollAttribute
```

创建Scroll滚动容器。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export declare function Scroll(    scroller?: Scroller,     content_?: CustomBuilder,): ScrollAttribute--><!--Device-unnamed-export declare function Scroll(    scroller?: Scroller,     content_?: CustomBuilder,): ScrollAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| scroller | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 |  |
| content\_ | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 子组件。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ |  |


## Scroll

```TypeScript
export declare function Scroll(
    style_: CustomBuilderT<ScrollAttribute>, 
    content_?: CustomBuilder
): ScrollAttribute
```

定义滚动组件。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**装饰器类型：** @Builder

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export declare function Scroll(    style_: CustomBuilderT<ScrollAttribute>,     content_?: CustomBuilder): ScrollAttribute--><!--Device-unnamed-export declare function Scroll(    style_: CustomBuilderT<ScrollAttribute>,     content_?: CustomBuilder): ScrollAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style\_ | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;\_\_\_MD\_LINK\_USD\_1\_\_\_&gt; | 是 | 创建滚动的样式 |
| content\_ | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | Scroll的属性。 |

