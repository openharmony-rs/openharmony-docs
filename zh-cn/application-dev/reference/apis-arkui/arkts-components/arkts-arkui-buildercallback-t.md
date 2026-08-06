# BuilderCallback

```TypeScript
declare type BuilderCallback<Args extends Object[] = any[]> = (...args: Args) => void
```

\_\_\_INLINE\_CODE\_DESC\_USD\_0\_\_\_是全局\_\_\_INLINE\_CODE\_DESC\_USD\_1\_\_\_函数的类型别名，作为\_\_\_INLINE\_CODE\_DESC\_USD\_2\_\_\_函数的入参类型，用于指定待封装的全局\_\_\_INLINE\_CODE\_DESC\_USD\_3\_\_\_函数。

**起始版本：** 22

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为22。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-declare type BuilderCallback<Args extends Object[] = any[]> = (...args: Args) => void--><!--Device-unnamed-declare type BuilderCallback<Args extends Object[] = any[]> = (...args: Args) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| args | Args | 是 | 全局\_\_\_INLINE\_CODE\_USD\_0\_\_\_函数的入参。\_\_\_INLINE\_CODE\_USD\_1\_\_\_采用剩余参数语法，允许传入任意数量的参数，\_\_\_INLINE\_CODE\_USD\_2\_\_\_表示这些参数的类型列表。不传入参数时，传入的参数列表为空， \_\_\_INLINE\_CODE\_USD\_3\_\_\_函数以无参形式调用。  |

