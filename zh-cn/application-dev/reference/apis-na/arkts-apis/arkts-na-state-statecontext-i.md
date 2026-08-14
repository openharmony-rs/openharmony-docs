# StateContext

Context of a state, keeping track of changes in the given scope.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare interface StateContext--><!--Device-unnamed-export declare interface StateContext-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## scope

```TypeScript
scope<T>(id: int, paramCount: int): IncrementalScope<T>
```

The scope which is used to track the changes of state context.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-StateContext-scope<T>(id: int, paramCount: int): IncrementalScope<T>--><!--Device-StateContext-scope<T>(id: int, paramCount: int): IncrementalScope<T>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | int | 是 | state cotext id |
| paramCount | int | 是 | the count of param |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [IncrementalScope](arkts-na-state-incrementalscope-i.md)&lt;T&gt; | return state scope |

