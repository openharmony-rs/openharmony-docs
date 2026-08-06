# Stack

## Stack

```TypeScript
export declare function Stack(
    options?: StackOptions,
    content_?: CustomBuilder,
): StackAttribute
```

堆叠容器，子组件按照顺序依次入栈，后一个子组件覆盖前一个子组件。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export declare function Stack(    options?: StackOptions,    content_?: CustomBuilder,): StackAttribute--><!--Device-unnamed-export declare function Stack(    options?: StackOptions,    content_?: CustomBuilder,): StackAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 设置子组件在容器内的对齐方式。 |
| content\_ | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | container |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ |  |


## Stack

```TypeScript
export declare function Stack(
    style: CustomBuilderT<StackAttribute>,
    content_?: CustomBuilder,
): StackAttribute
```

Defines Stack Component.

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**装饰器类型：** @Builder

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export declare function Stack(    style: CustomBuilderT<StackAttribute>,    content_?: CustomBuilder,): StackAttribute--><!--Device-unnamed-export declare function Stack(    style: CustomBuilderT<StackAttribute>,    content_?: CustomBuilder,): StackAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;\_\_\_MD\_LINK\_USD\_1\_\_\_&gt; | 是 | the callback to set up component's attributes. |
| content\_ | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | container |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ |  |

