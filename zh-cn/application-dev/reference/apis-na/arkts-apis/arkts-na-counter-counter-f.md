# Counter

## Counter

```TypeScript
@ComponentBuilder
export declare function Counter(
    content_?: CustomBuilder
): CounterAttribute
```

创建计数器组件。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@ComponentBuilderexport declare function Counter(    content_?: CustomBuilder): CounterAttribute--><!--Device-unnamed-@ComponentBuilderexport declare function Counter(    content_?: CustomBuilder): CounterAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| content_ | CustomBuilder | 否 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| CounterAttribute | The attribute of the Counter. |


## Counter

```TypeScript
@Builder
export declare function Counter(
    style: CustomBuilderT<CounterAttribute>,
    content_?: CustomBuilder,
): CounterAttribute
```

定义Counter组件。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@Builderexport declare function Counter(    style: CustomBuilderT<CounterAttribute>,    content_?: CustomBuilder,): CounterAttribute--><!--Device-unnamed-@Builderexport declare function Counter(    style: CustomBuilderT<CounterAttribute>,    content_?: CustomBuilder,): CounterAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | CustomBuilderT&lt;CounterAttribute&gt; | 是 | Counter属性实例。 |
| content_ | CustomBuilder | 否 | 子组件。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| CounterAttribute |  |

