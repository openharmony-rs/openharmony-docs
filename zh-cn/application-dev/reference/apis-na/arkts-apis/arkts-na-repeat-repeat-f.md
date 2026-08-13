# Repeat

## Repeat

```TypeScript
@ComponentBuilder
export declare function Repeat<T>(arr: RepeatArray<T>): RepeatAttribute<T>
```

Indicates the type of Repeat.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@ComponentBuilderexport declare function Repeat<T>(arr: RepeatArray<T>): RepeatAttribute<T>--><!--Device-unnamed-@ComponentBuilderexport declare function Repeat<T>(arr: RepeatArray<T>): RepeatAttribute<T>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| arr | [RepeatArray](arkts-na-repeatarray-t.md)&lt;T&gt; | 是 | The Data Source. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| RepeatAttribute&lt;T&gt; |  |


## Repeat

```TypeScript
@Builder
export declare function Repeat<T>(
     style: CustomBuilderT<RepeatAttribute<T>>
 ): RepeatAttribute<T>
```

定义Repeat组件。需要在组件属性设置开始时调用setRepeatOptions，并在组件属性设置结束时调用applyAttributeFinish。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@Builderexport declare function Repeat<T>(     style: CustomBuilderT<RepeatAttribute<T>> ): RepeatAttribute<T>--><!--Device-unnamed-@Builderexport declare function Repeat<T>(     style: CustomBuilderT<RepeatAttribute<T>> ): RepeatAttribute<T>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | CustomBuilderT&lt;RepeatAttribute&lt;T&gt;&gt; | 是 | 用于设置Repeat属性的回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| RepeatAttribute&lt;T&gt; | Repeat属性实例。 |

