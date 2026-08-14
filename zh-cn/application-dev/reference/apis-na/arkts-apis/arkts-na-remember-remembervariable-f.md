# rememberVariable

## rememberVariable

```TypeScript
@Builder
export declare function rememberVariable<T>(initialValue: RememberInitialType<T>): MutableVariable<T>
```

创建状态变量。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@Builderexport declare function rememberVariable<T>(initialValue: RememberInitialType<T>): MutableVariable<T>--><!--Device-unnamed-@Builderexport declare function rememberVariable<T>(initialValue: RememberInitialType<T>): MutableVariable<T>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| initialValue | [RememberInitialType](arkts-na-rememberinitialtype-t.md)&lt;T&gt; | 是 | 状态变量的初始值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [MutableVariable](arkts-na-remember-mutablevariable-i.md)&lt;T&gt; | 返回状态变量。 |

