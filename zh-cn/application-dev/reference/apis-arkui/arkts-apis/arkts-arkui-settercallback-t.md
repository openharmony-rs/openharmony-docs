# SetterCallback

```TypeScript
export declare type SetterCallback<T> = (newValue: T) => void
```

设置值的回调方法。

**起始版本：** 20

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为20。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-export declare type SetterCallback<T> = (newValue: T) => void--><!--Device-unnamed-export declare type SetterCallback<T> = (newValue: T) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| newValue | T | 是 | 要设置的新值，当绑定值被修改时传入此参数。 |

